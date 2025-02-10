# Smart Pointers

Wrapper class around classical pointers in C++ that automatically free the memory when it is not referenced anymore.

```C++
class LargeObject
{
public:
    void DoSomething(){}
};

void ProcessLargeObject(const LargeObject& lo){}
void SmartPointerDemo()
{    
    // Create the object and pass it to a smart pointer
    std::unique_ptr<LargeObject> pLarge(new LargeObject());

    //Call a method on the object
    pLarge->DoSomething();

    // Pass a reference to a method.
    ProcessLargeObject(*pLarge);

} //pLarge is deleted automatically when function block goes out of scope.
```

- `pLarge.reset();` gibt den Speicher frei, bevor der Pointer out of scope ist
- `pLarge.get();` gibt den Raw-Pointer zurück für Code der Intelligente Pointer nicht unterstützt


## unique_ptr

https://learn.microsoft.com/de-de/cpp/cpp/how-to-create-and-use-unique-ptr-instances?view=msvc-170
- Standardfall
- Hat genau einen Besitzer
- Besitzer kann gewechselt werden


## shared_ptr

https://learn.microsoft.com/de-de/cpp/cpp/how-to-create-and-use-shared-ptr-instances?view=msvc-170
- Hat einen Referenzzähler, kann also mehrere Besitzer haben
- Wird erst freigegeben wenn alle Besitzer out of scope sind
- nutze `make_shared` zum Erstellen
```C++
// Use make_shared function when possible. 
auto sp1 = make_shared<Song>(L"The Beatles", L"Im Happy Just to Dance With You"); 
// Ok, but slightly less efficient. 
shared_ptr<Song> sp2(new Song(L"Lady Gaga", L"Just Dance")); 
// When initialization must be separate from declaration,
shared_ptr<Song> sp5(nullptr); 
sp5 = make_shared<Song>(L"Elton John", L"I'm Still Standing");


// Erstellung bei gemeinsamer Nutzung von einem Objekt

//Initialize with copy constructor. Increments ref count. 
auto sp3(sp2); 
//Initialize via assignment. Increments ref count. 
auto sp4 = sp2;
```

- Übergeben by value ruft copy constructor auf und somit ist auch der Aufgerufene Besitzer
- shared_ptr sind Equal wenn sie auf das selbe Objekt verweisen


## weak_ptr

https://learn.microsoft.com/de-de/cpp/cpp/how-to-create-and-use-weak-ptr-instances?view=msvc-170
- Zeigt auf Objekte die von einem oder mehreren shared_ptr genutzt werden
- Ist nicht an Referenzzählung beteiligt (kann also ungültig werden)
- Wird genutzt um Zirkelverweise von shared_ptr zu verhindern

---

Origin: https://en.cppreference.com/book/intro/smart_pointers
References: 
Tags: 
Created: 27.09.2024

