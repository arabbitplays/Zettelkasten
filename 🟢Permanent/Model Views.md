# Model Views

- different roles of a project look at a system from different viewpoints as models become to complex to be understood by one person
	- information is distributed in different heterogeneous models
	- information between different models becomes redundant or dependent on other models
	- when changes hit, these redundancies can lead to inconsistency which invalidates the whole model

- <mark style="background: #FFB86CA6;">viewpoint</mark> - conceptual perspective used to address a certain concern (from where I am looking)
- <mark style="background: #FFB86CA6;">view type</mark> - set of metaclasses that are part of a view and a mapping to a certain concrete syntax
- <mark style="background: #FFB86CA6;">views</mark> - set of instances of a specific concrete syntax, results of the application of a view type to the system
![[Pasted image 20250315090457.png]]

- the <mark style="background: #FFB86CA6;">synthetic approach</mark> just model all views and relates them all to each other
	- <mark style="background: #FF5582A6;">high synchronization cost</mark>
- the <mark style="background: #FFB86CA6;">projective approach</mark> derives the views through some routine from an underlying source model
	- <mark style="background: #FF5582A6;">monolith structure</mark>

---

Origin: MDSD Vorlesung
References: [[Models]]
Tags: 
Created: 15.03.2025

