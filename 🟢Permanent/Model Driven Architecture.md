# Model Driven Architecture

- standard that uses [[Models]] to improve software development and architecture
- specifications should be machine readable
	- modern shift of what that means ([[Natural Language Understanding]]) but in practice still tied to formal languages
- models can be transformed to other models
	- because code is just a model too, this can allow or automatic code generation

- <mark style="background: #FFB86CA6;">Computation Independent Model (CIM)</mark> 
	- describes requirements and environment of the system
	- for example Use Case Diagrams
- <mark style="background: #FFB86CA6;">Platform Independent Model (PIM)</mark>
	- focus on the operation of the system, but no platform details
	- for example Component Diagrams
	- Together with a platform model, this can be transformed into a PSM
- <mark style="background: #FFB86CA6;">Platform Specific Models (PSM)</mark>
	- additional focus on the specific platform
	- for example Class Diagrams or Java Code
	- can be transformed into code

- In praxis, only repetitive code is automaticaly generated 
- This is then combined with generic platform code and individual code to create the system
![[Pasted image 20241025174049.png]]

---

Origin: Model Driven Software Development
References: [[Models]], [[Model Driven Software Development (MDSD)]]
Tags: 
Created: 25.10.2024

