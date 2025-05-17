# Smart Pointers

Wrapper class around classical pointers in C++ that allow for automatic lifetime management of resources.

## unique_ptr

- This one is for exclusive ownership, meaning the object is only ever referenced by this pointer, so it gets destroyed when the pointer goes out of scope
- <mark style="background: #BBFABBA6;">very cheap</mark>
- can be created using `make_unique()`
- the owner can be changed by moving the pointer (but can not be copied)
	- the source pointer is set to null after that
- it is easy to convert to a `shared_ptr` 
	- so it is a good choice for the return type of factory functions, as the caller can decide if it wants shared or exclusive ownership
```c++
template<typename... Ts>
auto createWidget(Ts&&... params) {
	std::unique_ptr<Widget> pWidget(nullptr);

	if (...) {
		pWidget.reset(new DerivedWidget(std::forward<Ts>(params)));
	} else if (...) {
		...
	}
	
	return pWidget;
}

// convert unique_ptr to shared_ptr
std::shared_ptr<Widget> widget = createWidget( arguments );
```
 - in the standard case, the object is destroyed with `delete`, but custom deleters can also be specified
	 - but they become part of the type of pointer
```c++
```c++
template<typename... Ts>
auto createWidget(Ts&&... params) {
	auto deleteWidget = [](Widget* pWidget) {
		makeLogEntry(pWidget);
		delete pWidget;
	}

	std::unique_ptr<Widget, decltype(delWidget)> pWidget(nullptr, delWidget);

	... // as before
	
	return pInv;
}
```

## shared_ptr

- creates a reference counter  (in an instance of a control block) for every object
	- decrement when a pointer is destroyed
	- increment when one is created or copied
	- when the counter hits 0, destroy the referenced object
	- <mark style="background: #BBFABBA6;">allows for fully automatic garbage collection</mark>
- can be created using `make_shared()`
	- <mark style="background: #D2B3FFA6;">should not be created from a raw pointer variable</mark>, because if this is done twice with the same raw pointer, two control block are created, the object is thus destroyed twice and undefined behavior emerges
```C++
// do this (or make_shared())
std::shared_ptr<Widget> spw1(new Widget);
auto spw2(spw1);

// instead of
auto pw = new Widget;
std::shared_ptr<Widget> spw1(pw);
auto spw2(pw); // creates a second control block
```
- in the standard case, the object is destroyed using `delete`, but here it doesn't effect the type
```c++
auto customDel = [](Widget* pw) { ... };
std::shared_ptr<Widget> pw(new Widget, customDel)
```
### shared_ptr from this

- shared pointers should not be created from raw pointers like `this`, because a soon as another shared pointer exists outside of the class, the creation creates undefined behavior through a second control block
- if pointer creation from `this` is needed, the class should inherit from `std::enable_shared_from_this`
	- to work this assumes, that a shared pointer exists from the instance => make constructor private and create through a factory function

```c++
class Widget: public std::enable_shared_from_this<Widget> {
public:
	// perfect-forward args to private ctor
	template<typename... Ts>
	static std::shared_ptr<Widget> create(Ts&&... params);

private: 
	Widget(...);
}
```

## weak_ptr

- use weak pointers for shared pointers that can dangle
- they can not be dereferenced, but they have to be converted to shared_ptr
	- while doing so, the weak_ptr checks if the object has been destroyed and return a shared_ptr if so
```c++
// creation from a shared_ptr
auto spw = std::make_shared<Widget>();
std::weak_ptr<Widget> wpw(spw);

// usage through conversion to shared_ptr
std::shared_ptr<Widget> spw2 = wpw.lock();
if (spw2) {
	...
}
```

- possible use cases:
	- interrupt shared_ptr cycles, as two shared_ptr pointing to each other are essentially a memory leak
	- for caching, as the cache can easily check if an objects it points to has been destroyed
	- for the observer pattern, to save the list of observers in a sender
```c++
static std::unordered_map<WidgetID, std::weak_ptr<const Widget> cache;

auto objPtr = cache[i].lock();

if (!objPtr) {
	objPtr = loadWidget(id);
	cache[id] = objPtr;
}
return objPtr;
```
---

Origin: Effective Modern C++ by Scott Meyers
References: 
Tags: 
Created: 27.09.2024

