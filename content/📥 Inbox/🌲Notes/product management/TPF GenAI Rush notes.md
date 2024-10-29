
[[+ TPF GenAI 1. Intro to GenAI - Sudalai Rajkumar]]

[[+ TPF GenAI 2. GenAI industry usecases]]

## 1. Intro to GenAI - Sudalai Rajkumar
- Evolution of AI
	- Timelines Trivia:
		- 1950-Turing test
		- 1956 - The term [[Artificial Intelligence|AI]] was coined. 
		- 1980's - AI winter
		- 1997 - IBM deep blue
		- 2011 - IBM watson
		- 2012 - Apple Siri
		- 2016 - Alpha GO beats world champion
		- 2022 - OpenAI's [[ChatGPT]]
	
- GenAI in [[Natural Language processing|NLP]] - [[Large Language models|LLM]]s
	- [[} Generative AI]] encompasses Algorithms that can be used to **Create** new content(text, audio, images, videos)
	- [[Large Language models]] are mostly based on transformer model by [[hugging face]], and are trained on Vast amounts of text data to generate human like text .
		- Language models are mainly Deeplearning based [[Neural Network|NN]] models 
		- The input for LLM's would be our query(in text format), and output would be the output text and Numerical embeddings. 
		- the sematics of LLM is that the input is called a `prompt`. 
			- Writing effective promts is called [[prompt engineering]]
			- Prompt engineering can have many approaches. Each appropriate for a particular usecase. 
		- Even if you are prompting LLM for something it hasnt been trained on, it can give an answer if you give an example
	- NLP evolution: 
		- Bag of words and ML models
			- Drawback: eg. if trained on the word `Happy` but is presented with `glad` in the prompt, it wont be able to give an output. 
		- Word vectors and Deep learning
			- In word vectors, individual words are represented in vector format, and words close together can be determined by a distance measure. 
			- compared to bag of words, we now know which words can be grouped together. 
			- Drawback: each word is represented by a vector, but contextual understanding is not there. 
		- Context vectors and Transformers
			- Entire sentence is being converted into a vector, and by this, model can understand **Context**
			- Transformer models are there since 5 years. What has changed is the output has become quite good because of
	- LLM Training process
			- 1. LLM pretraining
				- done to predict next word in a sequence. The model is trained on HUGE amounts of text data to do this. 
			- 2.Supervised finetuning & 3.reward modelling
				- Some supervised prompt and result feedback is done, post which reward based training on prompts is done on the model, by human based ranking of multiple output texts for same prompt. 
				- A seperate model is also trained in this step to score the output text given by the model
			- RLHF(Reinforced learning)
				- this is where the feedback from the 2nd and 3rd steps is fed into the model for further improving/finetuning it. 
				- Post this, process is repeated from step 2. 
- [[} Generative AI|GenAI]] in images - Diffusion models 
	- Examples are Stable diffusion, DallE. There is a free one on huggingface to play around with
	- How does it work
		- Diffusion models remove noise from an image, and at the same time, that processed image is discriminated. 
		- So a generator and a discriminator work iteratively to come to a final image. 
		- Initially, a random noisy image is provided to the generator, which is why same prompt can give different results when 
- Deep Dive into [[Large Language models]]
- Limitations and considerations
	- Limitations: 
		- Knowledge cutoff: Trained only upto a certain date
		- Ambiguous inputs. Garbage in Garbage out
			- (however, there is rarely also the limitation of Ambiguous output)
		- Hallucinations(interesting, read more about it)
			- when the output is entirely made up, without any basis in fact. 
			- This is especially for factual information. less for prompts like `assume the persona of Steve Jobs`
		- Privacy issues. 
			- You should not ever give your personal data to LLM's. Or it will be included in its training data, and anybody can access it in the next version of the LLM. 
		- Performance and latency issues
			- Keep this in mind when crafting any API which calls GPT API. 
			- Also keep cost in mind, it can quickly run out of hand 
		- arithematic and logical issues
- LLM ecosystem: Some tools to use for overcoming LLM limitations: 
	- Prompt engineering: zero shot, few shot, chain of thought, self-consistency, tree of thought, re-Act, graph
	- Vector databases: chrome, Qdrant, weaviate, pinecone
	- Orchestration: Llamaindex, lang chain, Chat gpt
	- others: H2O LLM studio, portkey, guardrails AI
	- LLM Api's from : OpenAI, Cohere, AnthropIc, hugging face

## 2. GenAI industry usecases

- Basic principles: 
	- GANs- 2 NN's , a generator and a discriminator working against each other iteratively to come to a final output. 
	- Transformers - NN that can understand context in a sentence and generate subsequent text appropriate to the context. 
- Usecases: 
	- GAN's 
		- image synthesis and generation
		- Text to image synthesis
		- data augmentation
		- style transfer and editing
		- Examples: MangaGAN, Medical image synthesis
	- Transformers: 
		- Used mainly in [[Natural Language processing|NLP]] application s such as: 
			- Language translation
			- text generation
			- summarization
		- OpenAI's GPT and LaMDa are (in)famous examples
- Communicating with AI
	- Prompt engineering: write effective instructions to AI models in not-so-plain english
		- briefly, a good prompt for 
			- text-to-text models should have $\rightarrow$ instruction, input text, context(or examples(optional but advised)), formatting requirements(optional)
			- Text-to-image models should have $\rightarrow$ instruction, Details, style or mood

> [!Hint]
> 	- Make your AI art stand out: Use Midjourney Reference sheet or MidLibrary.io
> 	- You can also visit a prompt marketplace eg. Promptbase.com


- Evolving GenAI usecases. (categories)
	- language : LLM's, second brain, synthesis and generation, code development, AI reasoning
		- >Hint: You can run LLM's locally. For privacy and for using local knowledge bases(PKM)
	- Visual: synthetic media, 3d models, procedural generation(gaming), AI editing
	- Auditory: music generation, Voice generation(eleven labs, )
- Text synthesis: using LLM's to generate Human like text. 
- Playing around with Midjourney. Some tips
- The creative industry
	- content generation
	- digital art and design
	- film production instructions
- catch up with AI: Automate yourself, create MOC's, focus on creation and curation
	- advanced: Learn autoGPT and creating AI agents, localised personal LLM's, learning and mastering stable diffusion
- Jobs created by GenAI: 
	- prompt engineering, ai ethicist, ai model engineer, ai trainer, ai data manager, conversational ai designer. AND MANY MORE TO COME. 
- 

## 3. GenAI for multimedia

- AI evolution:: Prediction & forecasting --> analytics and optimisation--> GenAI
- tip: learn to use huggingface 
- tip: promp engineering(chain of thought prompting)
	- additive prompting. example using midjourney
- ANthropic demo
	- analysing Youtube financials 
- Using plugins with ChatGPT 4
	- prompt perfect
- Rephrase AI demo
- Startup tips
	- b2b enterprise sales tips
		- cadbury Ad

## 4. Streamlinging communication workflows

- Why communication industry is at an inflection point
	- pandemic, new way of working
	- accelerating cloud adoption for comm sw
	- conversational data not used is essentially lost
- existing comm workflows: onboarding, webinars, sales calls, customer success, support
- Human interactions with communication data: channel examples
- Enterprise AI stack for conversational data
	- speech tasks: ASR, translation, speaker separation, redaction
	- discriminative tasks: entities, sentiments, classification of intents, topics
	- Generative tasks(evolving): summarization, content creation, search, co-pilot
	- Supporting AI infra for predictions and recommendations and integration into existing data pipelines 
- Existing AI experiences vs GenAI : search, conversations, Knowledge management, content creation, personalisation, qna
- The landscape: brief overview: enterprise applications, tooling, domain specific models
- things to consider: 
	- build vs buy
	- trust and predictability
	- Product-market-sales fit
- all about symbl: visualising calls, 
- Workshop: 

## 5. Building QA(question-answer) systems. 


> [!TLDR] opinion
> **Webinar is a little too complex to understand properly**
> Use Llamaindex Documentation to understand in depth

- Context on LLM's. (repeat info)
- challenges of in-context learning
- LlamaIndex: central interface of all data sources(pdf's, excel's, databases, etc) of an org so as to reduce cost and latency to build LLM apps. 
	- Offers **data connectors** to ingest your existing data sources and data formats (APIs, PDFs, docs, SQL, etc.)
	- Provides ways to **structure your data** (indices, graphs) so that this data can be easily used with LLMs.
	- Provides an **advanced retrieval/query interface over your data**: Feed in any LLM input prompt, get back retrieved context and knowledge-augmented output.
	- Allows easy integrations with your outer application framework (e.g. with LangChain, Flask, Docker, ChatGPT, anything else).
- Retreival augmented generation. 
	- indexing stage
		- data connectors
		- documents/nodes
		- data indexes
	- querying stage
		- building blocks: retreivers, node postprocessors, response synthesizers
		- pipelines: query engines, chat engines, agents
- ![](https://i.imgur.com/8mDVQCj.png)
- Vector store index: raw docs stored in nodes in vector store each indexed with an embedding
- From the above, response is synthesized. 
- Demo given on ipynb notebook 
- Buildig a Unified query interface is the additional layer on top of all of this. 



## 6. AI chatbots, Virtual assistants

- What can AI chatbots accomplish: 
	- Evolution of support: buttons, extraction, free flowing text
	- urban company has search
	- order creation
	- Better engagement
	- cancellations
	- feedback
- 3 capabilities of GenAI: 
	- Generation: copywriting, images, video
	- extraction: resume parsing, summary, search
	- classification: customer reviews, spam, CRM
- Guardrail metrics are those which are used to make sure your model doesnt run amok when optimising for one north star metric
- What does Guardrails do? some examples
	- competitor: prevent your Upgrad AI from recommending coursera course. 
	- sensitive info
	- prodct info
	- theme relevance
- Companies want guardrails for their AI products to guard against certain things like above. 
- Chariots: help customer go from A to B
	- mirroring: if AI is mirroring everything you say. 
	- optimal policy decision: 
	- rewards
	- Nudges
	- Social proof
- Demo on Workhack Labs. 


## 7. Connecting LLM's to data via semantic search

- applications for organisations
- Text understanding x Generating 
	- Search--> Analyze --> generate
- architecture overview
	- ![](https://i.imgur.com/46aKqEG.png)
	- demo <http://co/rag>. Not available publicly. running on 
- Issue with lexical search
	- Distance between even unrelated words is sometimes similar to distance between related words. eg. cats, cat, bike
	- The solution for this has been stemming, 
	- eg. exact keyword is required for search
	- requires spell correction for any level of usage
	- Wikipedia is an example of a bad example of lexical search
	- Popular search engine Elastic search based on Apache Lucene is lexical search
- Multilingual lexical search is even more messed up. Index for each is different, and its super painful to set up spell correction to any level of scale. 
- Semantic search: 
	- similar words are much more close. 
	- demo: Comparison between the both
- Core concepts: 
	- Bi-encoders used for relevant words. 
	- ![](https://i.imgur.com/ySMw7QI.png)
- ALso good for multi-lingual search and cross lingual search
- How to train Embedding models for this? 
	- Multiple negative ranking loss(too complex for notes)
	- For multilingual and cross lingual search how can this be done? 
		- Use GenAI for simplifying embedding generation process
	- 
- Language bias
	- what is is? English words cluster around english words, russian words around russian
	- good or bad
		- side effects with
		- without language bias(shaadi should return indian wedding, but returns wedding in a church)
	- accessing language bias: cross lingual retrieval
- Challenges in semantic search
	- mid point between 2 points in vector spaces are quite confusing
		- in e-commerce: multiple topics causing erroneous results
	- Multiple fields: hard to satisfy all fields accurately
	- Long documents: context limit of transformers. 
	- Preferences: might never be able to cater for this. 



## 8. Create your own GPT

- Demo for H20.ai. 
	- comparison between different LLM models
- Generative AI models, Discriminative models: Already covered
	- Usecases: Text, image, code generation
	- history, baground, etc. 
	- emergent abilities
	- in context learning
	- external API's
	- Building blocks of LLM's
		- foundation: next token prediction
		- Finetuning: Instruction finetuning
		- RLHF: Aligning the model to humans
		- Database: leverage your own data
		- Memory: give external memory using Vector DB's. 
	- demo: Lens research 
-  Demo to create your own your own GPT using LLM studio. 
	- All fields to be customised, and priority
- H2O models on Huggingface 
- Problems with Closed source solutions
	- data privacy and security
	- dependency and customization
	- cost and scalability
	- access and availability
- Advantages of open sourced LLM's
	- data governannce
	- cost effective
	- flexible
	- Tunable
- How to follow the AI space:: some tips. 
  END
