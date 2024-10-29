---
tags: 🧠️/📥️/🎥️/🟥️
publish: true
aliases: 
type: video
status: 🟥️
---

- `Title:` [[+ Vector search Relevancy_Does the model  matter_DataJedi]]
- `Type:` [[+]]
- `Tags:` 
- `URL:` <https://www.youtube.com/watch?v=AGBQx2vvbE8&ab_channel=DataJedi>
- `Channel/Host:` Data Jedi
- `Reference:` 
- `Publish Date:` [[2023-10-11]]
- `Reviewed Date:` [[2024-09-21]]

---

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/AGBQx2vvbE8?si=5bdlpzPjNRKYk8vi" title="YouTube video player"  frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>


---

- ![](https://i.imgur.com/YRWJgeu.png)
- Testing out if using *different embedding models* impacts relevancy. 
- Search flow: 
	- Offline process: OCR is performed on tariff docs and **embedding model** generates embeddings stored in vector db. 
	- Online process: 
		- User performs search. The query is converted into an embedding. 
		- Similarity search is performed, across vector DB. 
			- Similar documents are retrieved, 
		- Retreived documents are enriched either using metadata or enhancements from an LLM
			- eg. summarising documents retreived, 
- models used: 
	- ![](https://i.imgur.com/E9JK5dR.png)
- Conclusion: Embedding model matters. 
- 

