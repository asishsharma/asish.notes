




### Dump
*  YTConnecting LLMs to data via Semantic Search TPF talk by Nils Reimers, Director of ML, Cohere.ai
	* notes: 
		* Brittleness occurs when **any algorithm cannot generalize or adapt to conditions outside a narrow set of assumptions**
	* Screenshots: 
		* ![](https://i.imgur.com/eHzWnj9.png)
		* ![](https://i.imgur.com/0MVsqFr.png)
		* ![](https://i.imgur.com/sA160IL.png)
		* ![](https://i.imgur.com/FnijUW3.png)


	* transcript
		* I hope all of you are doing great uh great to see you so many of you here this evening can you please give me a quick check if you can hear and see me fine just drop a thumbs up react and I'll know perfect perfect I see so many of them so many of them awesome awesome perfect let's let's go we are almost pretty much uh at the end of the cohort uh this is the second last uh session and uh I didn't realize where two weeks passed every every cohort that we run is filled with so many uh speakers coming in so many learnings packed in in those few weeks uh that
		
		it's hard to recall how fast the time goes but uh huge huge shout out to our
		
		partners as always uh Nexus Venture Partners who have been co-powering this entire series uh and the build-a-thon
		
		with us and our partners airmeat H2O llama index Microsoft for startups
		
		Postman refresh.ai work hack and V work labs I couldn't have done uh this
		
		without them so huge huge shout out to each uh each one of these Partners uh I
		
		think you've got a chance to interact with many of these Founders during the court as well and during the upcoming
		
		build upon you get to meet them in person also so thanks again to all our partners and before we kick start
		
		today's session I have a quick Poll for all of you I'll give more context about this fall in the next slide but tell me
		
		who all are coming to Bangalore tell me in the chat just write down the number yes I am if
		
		you already live in Bangalore what's in Bangalore uh I think you uh
		
		I definitely hope no one uh answers third because uh we have been running
		
		this course in the last two weeks and I definitely hope you know what's happening in Bangalore I see a lot of
		
		force cannot cannot this time but I see a lot of one and twos as well so
		
		uh yeah we like you all know we have the Gen AI Rush build-a-thon happening in
		
		Bangalore uh this 29th and 30th of uh July by the way today is the last day to
		
		submit your ideas if you haven't done so please do so uh please do that right
		
		after this session so that you don't miss out a lot to uh lots to win during the uh during the build-a-thon but more
		
		than that you will get to build products using your learnings that you uh gain throughout the cohort right so this is
		
		going to be an amazing experience uh you can win up to six lakhs INR and up to 2
		
		uh two and a half thousand dollars worth of open AI credits so uh tons of
		
		different teams have already participated we have so many interesting ideas coming in already but today is the
		
		last day for those of you haven't or those of you who haven't participated yet so make sure you submit your ideas
		
		at least you'll then be eligible to Avail open AI credits so make sure that
		
		you submit your ideas and get up for this build-a-thon because I am personally super excited to be a part of
		
		this and uh I'll be in Bangalore as well so uh I definitely hope to see many of
		
		you there uh in the coming weekend right so super excited for the build-a-thon uh
		
		we'll share the links uh all the relevant links in the chat as well some of you have been asking uh how to
		
		register but we will share the registration links as part of the process but uh yes wall joined akshat's
		
		session I was watching it from the sidelines and loved this session entirely I see a lot of you have have
		
		been posting notes about it as well uh on socials but if you like this session please drop a hard react so that we can
		
		know uh you enjoy the session as well all of these sessions we try to bring in uh Founders and Senior folks who come in
		
		and share their learnings with you uh so I definitely hope you like this session as well uh I see a lot of love for that
		
		in the chat uh also but uh yes I hope you are ready for the journey I Rush
		
		challenge as always all that you need to do is pay attention during the session take a lot of notes ask questions uh to
		
		the speakers and create your notes and share it on social right that's pretty much all that you need to do and
		
		obviously use the hashtag and learn with tpf and uh tiger social handle so that
		
		we know it's you and that's that's all that you need to do and lots of prizes
		
		to be one uh TPS swag kids uh charging plus me journey and AI subscriptions
		
		swiggy treats after every session and jamai Rush cohort Academy access as well
		
		so our tons and tons of different prices uh to be won during the cohort as well
		
		as during the build-a-thon so make sure that you are participative in uh all of this right and we have all we start
		
		sending out TPS circuits and um completely Amazed by the response
		
		that we have been getting from people who have received it this is uh in the
		
		process right now so many of you will be receiving it going forward as well some of the shipments are already out and
		
		some of you will start receiving this in the next few days so keep an eye out uh
		
		for this and yeah awesome I see I think uh
		
		in the chat a lot of people are expressing that they can't be in Bangalore this time but uh but yeah
		
		we'll try live streaming it for folks at least the demos for folks who are joining in uh from different parts of
		
		the country but if you're in Bangalore or if you are trying to uh or if you are
		
		trying to travel uh I definitely can assure you that will be worth it you'll be an amazing company uh with good
		
		mentors jewelry speakers and obviously fellow Builders will be there along alongside you uh hacking it away for uh
		
		for an entire day right so let's uh let's get up for that but uh but before
		
		that and without further Ado uh let's move on to today's session
		
		folks today we have with us Niels I'll just bring him onto the stage uh so
		
		he'll be on the stage in a few minutes but he's joining us from Frankfurt today and news is the director of machine
		
		learning at cohere.ai which is in the business of empowering developers and companies to level language AI uh
		
		previously he has a LED teams at hugging face where they have done some cutting as research in this space uh as also
		
		super excited to have him uh here with us today this session is going to be slightly technical so pay extra
		
		attention and now as always take notes and ask a lot of questions uh Niels
		
		welcome welcome to the product folks how are you doing today all right doing good thanks so much for
		
		for having me here um yeah we're all excited about generative AI
		
		um coheres is quite a big play on the space um as also as I will present like
		
		especially in the Enterprise case so this might be a bit overlooked
		
		um by people because yeah everyone knows open AI because I have a strong focus on
		
		end users students helping them on writing assignments um we all hate writing assignments so
		
		why should I write the 1000 essay about the French Revolution or the American
		
		Civil War or whatever topics you have um so here's a bit different we're
		
		focusing on the Enterprise case so go to like really large scale Enterprises and see how we can deploy
		
		generative AI there with our own foundational models and there you have like yeah really interesting challenges
		
		problems um so so if there's a hallucination and you're writing assignment about the French Revolution
		
		and no one cares because the teacher is not really reading it when they are grading that but if you do gen AI for I
		
		don't know let's say New York Times and there's and then they put out a article stating
		
		wrong information about I don't know Donald Trump or some conflict
		
		um this is like really really high stakes and so you're really excited to give a bit Glimpse often inside what
		
		we're working on absolutely and super excited to hear everything that you have to share uh
		
		tonight uh folks uh Niels is someone who has been on the research side as well
		
		for a very long time so lots to learn from him today make sure you take a lot of notes uh Nails over to you I'm around
		
		if you need anything but uh I'll I'll see you during the Q a over to you
		
		oh yes sir during the presentation I can't see the chat um if there's something yeah
		
		just just unmute interrupt if there's some questions or so also free I'll feel free to unmute and interrupt
		
		um I'll call out here cool so yeah as mentioned I will talk about semantic search
		
		um spit the bit overlooked young sibling of generative AI but yeah it allows really
		
		cool applications so first and what exactly here what we do is we train NLP
		
		foundational models as a server and provide them as a service so my colleague Phil
		
		um he's doing the generate model and we all know it you go go there you
		
		ask like hey write me an essay a thousand words on the French Revolution and then yeah generates you the text
		
		in a bit more professional environments people often use it to summarize um so so give me a summary of all the
		
		news on Apple from today um writing support or extraction so here
		
		are like news articles can you extract all the companies I mentioned in these text understanding is my area so I'm in
		
		charge of training the foundation models there um I'm not producing any new text but I'm
		
		my goal is to understand text so analyze text for example you do classification so given a news article
		
		um based on the news article is the credit default risk for company increasing or decreasing so if there's a
		
		big lawsuit there's like really high at risk for the company if they get like a big customer big client that's like
		
		beneficial other big use case a search you have like thousand millions billions of
		
		documents how can you find the right information within milliseconds
		
		and yeah we all know generative AI for these generic things like hey write me
		
		an essay about the French Revolution or um hey how can I use I don't know SK
		
		learn to do clustering of my data
		
		um so here worked really well when it's like generic public knowledge but in Enterprises you're often interested in
		
		like these these private information like hey what do our employees think about our benefits or what have we
		
		discussed with client X so far well how can I deploy service X in our cloud
		
		and luckily the out of the box generative AI models don't don't know this so so luckily they don't have the
		
		insights and the companies they have not sneaked in like all the information about all employees in every company
		
		and so right now they totally fail on these and people often think okay you can take
		
		them and fine-tune them on all the data a company has but then it's it's yeah
		
		that's really hard I'm really breath often the model fail fails and breaks and because yeah the
		
		the model training is kind of like yeah brittle and also updating is a challenge so when
		
		I want to do like hey what have we discussed was client X so far I don't want the information with a knowledge
		
		cut off in 21 but I want the information from like today or maybe like 10 minutes
		
		ago like what have I discussed like 10 minutes ago was the client Excel file what did they mention
		
		and one use case here um or what works here is is to combine text understanding was generate
		
		so you do um what do our employees think about our benefits or what has been discussed with client X so far so you
		
		first search then you analyze um that the results and then you generate
		
		the response and you say Hey you have discussed so far with the client in the next meeting you promise to follow up on
		
		and in general how does it work um so you start with these requests for
		
		example give me a bullet point list how the head count for the five biggest U.S tech companies changed during covert
		
		and then at first goes to our query generation model it generates a lot of queries it just pings external internal
		
		apis databases gets all the data you have like from Google search Bloomberg
		
		internal docs internal papers sentiment comments from investment
		
		analyst passive through a re-ranking stage that yeah filters all the output and says
		
		okay which what is relevant what's not relevant and then thus input this into the generation model to then
		
		um get create the generated text um out of it and yes it's kind of really cool to to
		
		do this so for example here's the demo we have what you you can ask is like what is the AWS free tier
		
		and then [Music] um that the model starts to search so here
		
		Google search search for like AWS free tier and then gets the information from
		
		Google add citations to it so it's not to prevent hallucination it says Okay
		
		um calculated each month across all region and I'll climately apply to your bill you have like two sources for that
		
		um which you can then verify that this is correct and what you can do is like do follow-up questions so for example
		
		how many hours can I use Linux
		
		so here then the model is smart enough that it's not like trying to search like
		
		Google search like how many hours can I use Linux which is like
		
		um yeah what you get free like really strange results when I was yeah okay here you're on the AWS context you're
		
		interested in the AWS free tier so it um adds the information that you're
		
		interested like how many hours can I use Linux on AWS free tier and then you can
		
		also ask like can I also use it for Windows foreign
		
		where it then starts to search okay how are hours of windows in the AWS free tier and then it gives you again the
		
		information that you can use eight hours free tier with Microsoft Windows Server 2008 uh based on the source and then if
		
		you want to verify it you see okay yeah he had mentions you can now use it for Microsoft Windows 2008.
		
		where's the so a big use case here is a search
		
		um and yeah I want to focus a bit more on the search use case because what's what's really critical is that you get
		
		the right information so so if you have a problem like hey give me a bullet point list how they had
		
		come for the five biggest U.S tax companies change during covert if you don't get the right information in it
		
		just the the model is obviously not possible to generate this and it also does not make really sense to create
		
		generation model that's yeah knowledgeable about all topics because we have constantly changing topics
		
		um if you ask like what's the most valuable tech company in the world this yeah
		
		quickly can change within a quarter sometimes because in weeks so so it more makes sense to have
		
		it hooked up to a search system that provides you up-to-date and correct information and how do you search and that's that's
		
		the most focus of the rest of the presentation and in search for a really long time
		
		people has been using lexical search so we all know it if we open a PDF if we open a Word document and we press Ctrl f
		
		we're able to find for the words and then this this gives up the results and one challenge here in Mexico search is
		
		like you take all the words and you create a vocabulary out of it so you count all the words for example in
		
		English say okay you mapped the word cat to the first position the word bike to the second position and the word cats to
		
		the third position and then internally for the machine it's represented like this so here that's the
		
		first that's the second that's the third word challenge here is that that there's they
		
		have like all the same distance so the distance from cat to cats is like a Hamming distance of two so they are like
		
		different in two bits a cat to bike and cats to bike also has a Hamming distance
		
		of two so then the model is not really able so if I search for the word cat and the
		
		document contains the word cats it's not able to find the information and so traditionally what people do is
		
		they apply stemming and so they go in and say okay we remove all the suffixes so if cats is there
		
		you'll remove the suffix so that it rewrites the the text into cat so if I
		
		search for cat I will find documents um talking about cat and cats
		
		um this works kind of well unless your company with things
		
		so so if you remove here the suffix ings you will so so if you search for
		
		like what things will remove the suffix imgs and you will find all documents containing the word with
		
		and you're like wondering okay I'm searching for this one particular really special company why do I get like
		
		totally arbitrary random results um Second Challenge in Mexico search is
		
		um spelling variations British English American English for example for the word color do you write it o r or o u r
		
		um again in lexical search these are two completely independent words they have the same distance as color to bike so it
		
		cannot differentiate if you're writing cholera or color or if there's a bike so
		
		it will just if you search for the American English Color it will just find documents on American English Color
		
		and tell you what you do here is you create a synonym list so you go in your
		
		text and you replace the word color with the British color you replace USA was
		
		United States of America and NY was New York and then you create like a really long synonym list and you try to cover
		
		most common synonyms um to to yeah to to cover this so that
		
		if you search for color you will find the white color if you search for NY you will find documents talking about New
		
		York third challenge um words can be complicated especially
		
		some some names can be really hard to spell it correctly so here we have two
		
		users want to book a trip to Honolulu go on my location so they try to spell it
		
		like Honolulu where they don't find results they try to spell it Honolulu
		
		again it's misspelling don't final result and then they back up and yeah
		
		try to search for Hawaii but again misspelled Hawaii and then Jay yeah just churn and say okay this is sadly not a
		
		usable search function I will not buy a product from you and here what people typically
		
		traditionally do is like spelling correction we all know this Google did you Ma mean to search for Hawaii and
		
		then giving you the correct spelling for Hawaii
		
		um final issue was lexical search is um MB chords the word Apple it can refer
		
		to the food what can refer to the company and the apple and apple pie and the apple and Apple Store those is like
		
		con hence the word Apple Bose is mapped to the same position in the vocabulary so if you search for apple pie it can
		
		also find documents mentioning um or talking about the Apple Store
		
		and yet totally in lexico search you just ignore this and say okay you don't
		
		do this and this explains why so far like 98 of the search systems
		
		were extremely terrible so here we have Wikipedia one of the top 10 most popular
		
		websites on Earth 20 years of experience visited by
		
		billions of users each month and if you have a really simple search query what is the capital of the United
		
		States and first entry is about capital punishment in the United States because it contains the word capital
		
		several times contains the word United States several times contains what states contains the word the and is and
		
		so he adjusts things okay these words really appear really often in this article this must be perfected for you
		
		and the article on Washington DC it's not shown on the first page it's not shown on the second page it's only shown
		
		I think on the third page but yeah it's there are not that many users that go on the third page for
		
		search results and so even such that Wikipedia is so popular the search
		
		system is completely broken and not usable because it's using lexical search
		
		and not able to understand that capital punishment and capital of the United States
		
		um have really different meanings and how can you make it worse
		
		um so there's not only English especially in
		
		India there are like so many languages um and and totally all these approaches
		
		in lexical search they they are language specific so tokenization in English you
		
		can tokenize on white spaces but in other languages Chinese Japanese they're
		
		like no space between words removing of the suffixes it's different
		
		in English to Spanish to Chinese stop words are different spelling Corrections has different synonyms are different
		
		um only to go to like different databases which you need to scale like how much data do I have in English how
		
		much data do I have in Spanish how much data do I have in Chinese um then you have like challenging
		
		documents with like mixed language people mixing English and Hindi for example together and then the question
		
		okay should I go the English Pipeline and tokenize them stop words synonyms
		
		spelling correction in English or should I go to Hindi or should I create like some English ID combination of that
		
		and if you do this for hundreds of languages it's super painful to set it up
		
		and really hard to optimize so so what you often see is people optimize sadly
		
		just the English pipeline so they're adding like spelling correction to English but not for for the other
		
		languages a topic that yeah my research group
		
		started to work on and invent and contribute a lot it's like semantic search
		
		um so semantic search the the fundamental idea is that you don't see words as like Atomic symbols that have
		
		like a position in a vocabulary and all have like the same distance but words have a meaning they have a
		
		relationship so for example the word color color and colors even such all three are spelled differently
		
		um they are really really close in the meaning and similar cat cats and kitty cat and kitty completely different
		
		characters completely different um yeah spelling but they they refer to
		
		the same also cat and dog canvas yeah be similar so suppose they're like popular
		
		household pets and apple and apple pie has a different meaning than Apple Store
		
		so so the idea of semantic search is to yes that was words
		
		and try to get like all the relationships that we have in language like color and color and colors
		
		like similar plural um all animals all household animals all
		
		animals Christopher and and project them in such a vector space so that that yeah
		
		the distances in these Vector space have a meaning and then you go from a sentence level uh from a work level to a
		
		sentence level to a paragraph level to a document level and this gives you a really good search
		
		system let me um share your day more so here we have
		
		asked a question on Wikipedia how's the weather in Toronto so could you hear us headquartered in Toronto and you want to
		
		go there in summer but not in winter so you search like how's the weather in Toronto on the one side we're comparing lexical
		
		search by elasticsearch and yeah the top one entry here is studying how the weather works on other planets has been
		
		helpful in understanding how the weather works on Earth because the this paragraph contains the
		
		word weather really often and and the the you're searching for weather so it
		
		thinks that that weather is a great hit here and as we see all the search results are
		
		like talking in general about the weather in contrast if you do semantic search
		
		and use a powerful model as provided by code here and you get a really good
		
		um hit so the first hit is like the city experience four distant Seasons Wisconsin little variance in length so
		
		it knows okay this this sentences paragraph answers the question how's the weather in Toronto
		
		um similar for other questions other um um other topics when you say okay what
		
		is the capital of France [Music] um
		
		lexical search things Republic of Congo is a great hit because it contains the
		
		word France and yeah probably also contains the word Capital so it thinks okay that's a
		
		really good hit and then it talks about your difference Departments of France Kingdom of France France 24 Tour de
		
		France we see France Scotia French Colony Empire that's not really making
		
		the connection to Paris but again semantic search but really understanding what's the capital of
		
		France and Paris is the capital and most popular city in France is able to map
		
		these to the same like close in the vector space and give you like the the nice results
		
		that's really cool about semantics searches like be able to search across languages so when we go back to like
		
		um how is the weather in Toronto
		
		and we can't say okay let's search the um Spanish Wikipedia
		
		so obviously if we search the the West lexical search the Spanish Wikipedia you
		
		find some entries that contain like weather um or Toronto but that's not really
		
		meaningful in contrast um with semantic search you can find the
		
		relevant entries so the first entry is Toronto Winters occasional features short code snaps when was when maximum
		
		temperatures remove remain below -10 degrees Celsius so it knows okay when I
		
		asked how's the weather in Toronto here talks about the winter so that this is like a really good match and it even
		
		works um on like really distinct alphabets so if I ask like in English how's the weather in Toronto
		
		again lexical search just finds on the Korean Wikipedia articles with English
		
		texts but that's not like really connected to Toronto in contrast with semantic search you can
		
		again find like the information that Toronto has cool human climate and
		
		Exhibits typical thousand Canadian weather and yeah it's it's it's nice because it allows you to easily search
		
		also cross languages so I can search across like 10 different um language languages in Wikipedia and
		
		then I see okay here I find information from the Spanish Wikipedia from the English Wikipedia German Wikipedia all
		
		the way down to the Korean Wikipedia and yeah this this is obviously not
		
		possible with lexical search so if I search like how's the weather in Toronto just makes sense if my document is in
		
		English and yeah as everyone who grows up in an area where more than one language is
		
		spoken knows okay sometimes can be really hard we don't know if the the article in English or in my case German
		
		or in Hindi or in Korean or in Russian or in Arabic
		
		and yet by just being able to search in one query and match it to another query you get really nice good results on that
		
		so how does it work on a technical level um so idea here's
		
		um these Vector spaces so so what you do is you take all the paragraphs you have of Wikipedia and you project them into
		
		Vector space not to like a random Vector space but such that you capture like these
		
		um yes sensible meanings that you have like color color and colors like all year household pets down here
		
		and so you have like a massive big Vector space was like tens hundred millions of documents
		
		and then when a query comes in like how is the weather in Toronto
		
		you also projected to the vector space and then you look for like close points so so here for example it might be like
		
		the Spanish Wikipedia article about the web and Toronto here's the English one here's the Korean one here's the Chinese
		
		one and then you just say okay you look in this Vector space for the closest matches
		
		and this works yeah very well in case you like really good search results
		
		on a technical level um how does it work you you have some Transformer model like word you input
		
		the query you input the document this gives you so-called contextualized word embedding so it's
		
		first protects all the words into like such a space like color apple pie cats
		
		and so on and then you do a pooling operation which is just
		
		like a simple mean of all the the word embeddings and this gives you a vector and then you can compare the vector with
		
		cosine similarity which which matters the similarity of two vectors and this gives you at the underscore and then you
		
		can say okay for this query which documents have the highest similarity which should be shown at the top of the
		
		search results and this is really nice as shown for multilingual search because it's no
		
		longer grounded in vocabulary and in yeah words where you say okay these are
		
		all the documents that contain the word color in the American English version and these are the documents containing
		
		the words color in the British English version but everything is projected to the Spectra space
		
		and so you can do like in a multilingual Crossing or setup where you say okay two dogs in the snow it's projected here the
		
		German sentence for this is projected here Spanish Chinese sentence is projected here so if someone searched
		
		for this it's projected to the same point independent of the language and hence finds the information across many
		
		languages so this is super cool that it works
		
		um across languages it's also really nice because it's extremely simplifies your your pipeline so as mentioned
		
		before in lexical search you have like these 100 times so if you
		
		have 100 languages you have these hundred times for Wikipedia it's like I don't know 300 languages so you have
		
		like 300 times for every language you need to know like how do I tokenize that language how do I
		
		remove suffixes what are stop words what are synonyms how do I do spelling correction
		
		in doing this times 100 is like really really painful and then you need to Monitor and
		
		maintain and then say oh we got a lot of data in Korea and so I need to bump up the the copies of the Korean database
		
		now everything is a simple workflow you take your documents and queries can be in anything in more than 100 languages
		
		you send us to our embedding model it produces these points in the vector space like here all the blue points and
		
		then you store these two points in a vector database which yeah it's optimized to store them efficiently on
		
		your disk and then you you get like these really nice Crossing or search capabilities so
		
		here you search in Arabic what's the capital of the United States and it finds the correct information
		
		from for example the English Wikipedia now it gets a bit more technical to give
		
		you a glimpse how are these representation embedding models trained
		
		one the most common approach is to use constructive training also called multiple negative ranking laws
		
		so the idea is you have certain positive pairs so this can be acquiring answer
		
		pair or question and duplicate question or paper title and the paper abstract or
		
		like in an e-commerce setting aquarium a product you purchased
		
		and what you say is that Ai and p i so A1 and P1 should be close in Electro
		
		space so the queries of the question like how is the weather in Toronto and
		
		the respective Wikipedia paragraph should be close in the vector space where all the other paragraphs in
		
		Wikipedia should be distant and it's kind of comparable to like a
		
		multiple choice exam we had in school so you ask a question how many people live in Berlin you give like three answer
		
		options and then the model has to guess which is the correct answer option and it does
		
		the guessing by um yeah projecting all these the question and the options to the vector
		
		space Computing the similarity in the vector space so like how distant or how close
		
		um is the the anchor to the positive so how close is the question to the
		
		possible answer um computes the the similarities here and then say okay here's my prediction
		
		first has a similarity of 0.5 second 0.3 plus 1.1 and then you know um the first
		
		answer is correct so you'll say okay what I want is like an extremely high similarity between
		
		anchor one positive one and low similarity for for the others
		
		um um okay so
		
		um question is how can you do it in multiple languages and across languages
		
		and you can use the same approach like these question answer press um but yeah can
		
		can do it like across languages so that's what we have done last year so we went on the web we found a lot of
		
		question answer pairs from hundreds of languages and then on these billions of possible
		
		question answer pairs we removed irrelevant pairs so for example you have a question and a cookie consent Banner
		
		where you say okay that's that's not really good answer like um when you ask a question how do I
		
		use generative Ai and then the answer is like hey please accept our cookie terms
		
		um similar to like hey please sign up register here to see the answers so so we went in and removed these data
		
		automatically on the data set which becomes challenging if you do it across handled languages so like on a
		
		Chinese website how does it look like how's the website structured do they
		
		have also something like cookie content printers or please sign up please pay here to see it or do they have something
		
		other then we extended it to triplets to say okay here's a question here's an
		
		answer and here's like a negative one certain to make the multiple choice test
		
		a bit harder so so much I like random answer options to it but adding like
		
		hard answer options to it and then we yeah a lot of time is spent
		
		on my cleaning they're like false positive where we say okay here's a question but the answer is not really
		
		yeah no answer to your question or here's a question answer and the negative is not really like a negative
		
		but an alternative good answer to it so so we really need to clean this
		
		um at that scale you can't do it manually so there are like a lot of tricks to do it like automatically in
		
		different stages and at the end we had like close to a billion English triplets and close to
		
		half a billion non-english triplets and then we we trained the model to understand
		
		um Mark your questions and answers across all the languages
		
		an interesting topic on these multilingual approaches is the so-called
		
		language bias so language bias means that certain language combinations are
		
		preferred so for example here we see a model that has a really strong language bias or the red dots or English text
		
		the blue dots are Russian text every sentence is both available in
		
		English and Russian and so so why we see like all the English text is clustering here or the
		
		Russian Texas clustering here so with such a model if you would search in English it would prefer to achieve a
		
		result in English even such um there might be better result in a
		
		different language and so big discussion pointers like language bias it is it good or not
		
		if you have language bias the model returns language results
		
		that yeah they rank higher just because of the language so if I ask like how's the weather in Toronto it would prefer
		
		the English Wikipedia even such maybe there are like other yeah Wikipedia
		
		passengers that are better and you can argue for language bias so
		
		if I put in like a German query I likely like to read like a German paragraph on
		
		this um more than like a Korean paragraph because yeah if someone searches in
		
		German probably that person is fluent in German but it's not necessarily fluent in Korean
		
		and also you can ask in terms of confidence by the model it's easier to compare query and document if they are
		
		in the same language than a different languages due to like challenges and and in machine translation and
		
		it's kind of like losses especially like really if you ask for specialized terms
		
		um it's really hard to estimate if if they are relevant or not but there are also side effects if you
		
		say okay you take a model with our language bias let's say it's it's perfect it doesn't see any language
		
		information it Maps the text just based on the language just based on the the content
		
		and if you have such a model for example for image search and you search for the
		
		word wedding you might get a picture like this the man white man and a
		
		smoking and a black smoking or white woman in a white dress
		
		if you now search in Hindi so I hope the Google Translation is correct for wedding
		
		the model again doesn't know that this is Hindi and also retrieves the same
		
		image and and slightly someone who's searching and speaking Hindi has a
		
		background from India and yeah weddings look quite differently like the people
		
		and the dresses and and the ceremony looks quite differently in Hindi yes sorry in India than it looks like in in
		
		North America or Western Europe seminar if you search for like who's the president
		
		um you want the answer Joe Biden is the current president if you search in French if the model
		
		doesn't know that this is French um it will also return that Joe Biden as the current president so so it will lose
		
		the information on the language which can give a hint a clue um on the country of that person and the
		
		relevant information for that person so so it's also not perfect from a user experience to have a model without
		
		language bias and we did some tests on on language
		
		bias um so so we took a data set we machine translated it to like English and Arabic
		
		and then we did different tests say okay we search in English and the documents are English or we search in Arabic and
		
		the documents are in Arabic or we do like a mixture of the documents like 50 50.
		
		and here in the First Column we see the quality of the model if the model would
		
		have not a language bias all numbers should be roughly the same but what we see here like in if you
		
		search in Arabic and your document collection is a mixture of those we see Quite A Drop In Search quality so
		
		results that are less relevant or higher ranked
		
		um due to this this language bias in the model and and but yeah luckily we have
		
		like also a second option where um this language bias is like mitigated
		
		where the differences between these four settings is a lot lower where it can really see okay what's the most relevant
		
		information independent of the language and then you can think about
		
		um yeah how to model language preferences so maybe you say okay the
		
		user just understands English so you just show English results um or you do like some language
		
		detection on the query and then you say okay we we filter out remove any
		
		documents from other languages so so the stand really depends on your application and use case what you want
		
		[Music] so you see a lot of excitement about semantic search
		
		like live Vector databases or speaking quite popular with like high quite High
		
		valuations um often pitched as the backbone for generative AI
		
		but there are certain challenges in semantic search um where it's good to to know okay where
		
		does it work and where does it not work and one challenge is like multiple topics so let's say you have a sentence
		
		bananas are the most sold Foods you've projected up here in the vector space
		
		you have a sentence Facebook was founded by Mark Zuckerberg he projected down here in the vector space
		
		and then some crazy person has idea to concatenate these two sentences as okay
		
		Banners are the most sold food Facebook was founded by Mark Zuckerberg and the question is like what's the good
		
		point for this text should be like close here to the bananas then
		
		you you just can be found for search queries like what is the most suit or
		
		should you put it here to like down to Facebook then it can be found like who's
		
		the founder of Facebook but it can't be found like information of bananas or should you put it like somewhere in
		
		between but the challenge can be that in between the spot is taken so that here in
		
		between you have data um on a completely different topic about
		
		let's say I don't know about deep learning and then you search like okay what's the uh
		
		how how do I set my learning rate and deep learning and then yeah this this
		
		text is closed in the vector space and is returned by the model and yeah you get really confused users why when I ask
		
		about deep learning get information about bananas and Facebook
		
		and this is like a real challenge like in e-commerce so here there's a
		
		synthetic data set we have genes available in a certain size and available in
		
		different colors and if I search for like blue jeans the first hit okay it finds like a blue jean but second and
		
		third hits gives me off options that are just available in green yellow and orange and black pink red because the
		
		average of like green yellow and orange in this Vector Space is really close to
		
		Blue and same for black pink and red it's also really close to blue and then you get like extremely confused users
		
		um like okay why is showing me like a jeans black pink and red and other jeans available in green and blue
		
		um so so there's like a big big Challenge and due to these averaging
		
		um that we can't encode and say okay this genes is available in three quarters and two colors and this is
		
		available in four colors um it's just the average but the average here doesn't make sense to take the
		
		average of the color options to to represent it like this
		
		um another challenge is multiple Fields so in e-commerce um
		
		you have some picture of the product you have some text like levels 511 genes and
		
		then someone is searching for red Levis jeans so from the picture itself you can tell
		
		okay this is a red jeans but not necessary this was a Levis jeans from the title you can tell okay this is a
		
		Levis jeans but not that this is like in red and so so right now the models there's
		
		no model that's able to search across both like the image and the text
		
		to to be able to tell okay this is a red levels jeans and this should be like preferred to like other options from
		
		levels or other other genes from other vendors
		
		um challenges long documents um so so as we know Transformers for a
		
		long time they had a context length limit of 500 tokens and now we're able to push a bit further
		
		to like two thousand ten thousand twenty thousand tokens but even if we scale the context lengths
		
		of Transformers indefinitely it's not able to solve the problem of long documents so totally what customers have
		
		as document like this this the Johnson and Johnson 21 annual report has 140 Pages a lot of text
		
		um and as mentioned before we can encode in one embedding one topic so we can just encode like
		
		um like here bananas are the most so fruit or Facebook was funneled by Mark Zuckerberg but we can't encode those
		
		um and then the challenge like okay um if you have 140 pages that is
		
		probably more than one topic these are like hundreds of thousands of topics so it's not possible to encode it into
		
		like a single embedding so it's a big question it's like okay how can you take this document and represent it well
		
		in the lecture space final challenge is stretch preferences
		
		let's say you search for podcasts you have updates on AI you have two podcasts
		
		the AI update and last week in AI so you're probably based on the text match you would say yeah AI update
		
		that's really close to updates on AI it's closer than last weekend AI so you should rank this higher based on the
		
		text match but for users um just a text match isn't in the end
		
		not the main Criterion so so what users care about in podcast is like the release date and the rating
		
		and if you see this was released in May 2015 and got a one out of 5 stars
		
		and rating and this was like released in July this year got 4 out of 5 Stars so
		
		so lightly users prefer this because if I search for updates on AI I don't want
		
		to listen to a podcast that's eight years old and got like a very bad rating I want like recent podcast
		
		um that has a really good rating but yeah right now there's like no way how to represent this in a regular space
		
		so how can we put in recently popularity into this Vector space just on the text
		
		match which is in such a case like a terrible terrible idea
		
		coming to the conclusion so semantic search is amazing for multilingual setups you can use the same pipeline for
		
		all languages So within five minutes you get a system up and running and working
		
		that can search across hundreds of languages and it works well semantic search if
		
		your data can be presented as short paragraphs like Wikipedia you take all the paragraphs from Wikipedia and then
		
		you can index on this test challenges like in e-commerce we have like these
		
		different color options where you have information across the image across the title across the body
		
		and also ask challenges if you have like really long documents let's say you you do in the interview
		
		with different terms of different speakers so so this is right now still challenging to do
		
		um and yeah also other ranking signals are hard like how do you take popularity recency rating into account
		
		how critical is is the semantic text match versus the popularity was the the
		
		recency so so an intermediate hack is still um
		
		do some interpolation when you say okay the the semantic text match
		
		contribute 70 popularity contributes 20 reasons he
		
		contributes ten percent and then you do yeah weighted sum of these three features to give you the
		
		final results but still it's it's not yeah really good perfect version and the questions also how much do you care
		
		about recently how much do you care about popularity how much do you care about the exact text match so maybe
		
		you want to find this one AI update episode from 2015 that has like one out
		
		of five stars because you were really looking for this one episode
		
		um we're currently working on New Foundation models for search that are addressing these these topics
		
		um which which yeah are will be super exciting because right now semantic
		
		search works on like these really small subset on like text that can be represented as short
		
		paragraphs and yet we're working on on enabling models to take all these aspects into account and work really
		
		well on these great that's so much for my site looking forward to questions remarks you might
		
		have amazing thanks so much Niels uh this was
		
		a pretty complex topic but you did a fantastic job layering it with demos and
		
		contextual examples uh so this is super helpful I think everyone could follow
		
		through very easily we have tons of different questions but I think we'll be
		
		able to take the top top ones so I'll uh I'll pick the top questions and I would
		
		love to hear your thoughts on them so the first one is how do llms adjust
		
		their learnings based on Ever Changing data for example charge GPT is I think limited to a certain date but how do
		
		llms currently adjust their learnings Based on data which is like always changing
		
		yes so that's a challenge and we know chat GPT has the cutoff of 21 if you ask
		
		like who's the Monarch um of of the United Kingdom doesn't know
		
		that Queen Elizabeth sadly passed away um one approach is to try to continuously
		
		learn so you get continuously new data like news internet data and you try to
		
		train on this but this is I have the feeling like a dead end it's like really
		
		really hard to reinsure the consistency and quality because what you see is that
		
		you have like these catastrophic forgetting um that the model here forgets about it
		
		and doesn't follow anymore like these instructions also we see a lot of complaints
		
		um on like chat GPT gpt4 that quality degraded a lot and for some task
		
		accuracy quality dropped from like 98 to like two percent over the last half year
		
		which is like really really killing so you put something in production based on gpt4 you say okay that's amazing you get
		
		traction and then open AI doesn't update and now it just works in like two percent of your user base
		
		user will complain with you and and it's not a really good excuse to say yeah but it worked a quarter ago was open AI
		
		and so so I think that's a dead end what I like more is to
		
		get these GIF models the ability to use Google search or search
		
		so if you ask um like who's the Monarch from United Kingdom that you're not
		
		um go in and and have this memorized in the model but it just yeah use Google
		
		search like we do like we go in so I don't know the major and the president of every country I don't know who's like
		
		the major from daily or Bangladesh or it's also not expected that I know what
		
		if you ask me hey who's the current major of New daily yeah I just go search for It Go on Wikipedia and see okay
		
		that's the current nature of that City the current president of that country the current monarch of that country
		
		and then I'm able to to answer this and the nice thing is you can update it live
		
		updated like as soon I mean we know Wikipedia editors are crazy fast so as soon as soon as Queen
		
		Elizabeth sadly passed away like I don't know like five seconds later the Wikipedia article was updated
		
		this means such a model that works uses Google search is also updated within
		
		five seconds and you don't have to wait I don't know half a year until like a new version comes out
		
		absolutely but uh how do you see this space evolving because this is a very important feature uh being ever updated
		
		with the right kind of data right so do you think both of these will go hand in hand maybe a Google or Wikipedia will
		
		continue to exist in its current form meanwhile uh llms will also exist in a
		
		certain place how do you see this evolving in the next few years and
		
		yes also I think search systems like Google um well will stay relevant increase also
		
		in relevancy to provide like good search interface to up to date knowledge
		
		um Big Challenge right now for the models to know how to search how to re-parify
		
		something so so um to us so we are humans really good like
		
		it's an interactive process so it's not a one-off thing but it's like an iterator if I stretch something for
		
		something and see okay this this information um it's not relevant so I backtrack
		
		rephrase it see okay I got um part of the information and then I go to
		
		the next top so if you ask me from which high school did the major of
		
		Didi graduate from it's not what I would do like on a single shot but I would search okay
		
		who's the major of that City uh which graduate from which high school did this
		
		person graduate from and then I'm able to give the answer so so this is like an interesting Direction giving models
		
		ability to search and being able to backtrack and sadly
		
		right now we know all the problems with hallucination and make us makes up stuff so sadly models are really bad in
		
		deciding what do they know what do they don't know and that's kind of critical like for
		
		backtracking to say okay I don't know who's the major of that City so I need to search for this for so so
		
		if you ask like from which high school did the U.S president graduate I can't directly search a high
		
		school Joe Biden if you ask about like I don't know who which high school did the I don't know
		
		German president graduate from you might not know who's the German president but you're aware of like okay I don't know
		
		I'm not really 100 confident about the German president so I first search okay who's the German
		
		president and then I searched for this person and where where did this President go to school
		
		God it makes sense makes sense uh Neil it's one of the questions that we constantly keep getting in the
		
		communities how will AI impact a particular industry or a profession right we have all been hearing uh news
		
		about how our jobs will be taken away and stuff like that but in specific context to data science uh
		
		since AI involves so so much of data and adjacent areas right how will the data
		
		science Industry or profession be impacted with respect to AI
		
		I am not really says I don't Echo the the
		
		sentiment on like AI will replace us all and in two years there will be no
		
		software Developers I mean we had this in the past for several times people were still able to
		
		to shift and to get like more productive and this is like what we have in history
		
		I mean yeah they're like obviously some professions go away but then other
		
		professions pop up using this and seven data science and software development it will be the same so we
		
		see that these tools are really powerful uh what will go away is this person
		
		that's not using Ai and then will be replaced by someone who knows Ai and how
		
		to use AI and then this person becomes yeah more productive I think in general the number
		
		of the developers data scientists will not decrease um because yeah totally what we see is
		
		like yeah you get developers more productive but at the same time you have high expectations so I'm in like web
		
		development for 20 years like putting out a website 20 years ago
		
		was like really easy that's like here there's a form I don't know it shows you all the real estate
		
		um a real estate agency had and then you could click on it but now you if you
		
		build something like this with all the Frameworks you have you have like so many expectations where you can share it
		
		uh scroll it Infinity scroll live update inline editing and so on so so even such
		
		that web development became a lot more productive over the past 20 years
		
		it's not like that today I don't know you have like two web developers doing like all the websites on earth when on
		
		contrast it massively grow over time and same will be with software development data science with AI
		
		um it will bring in more and more people to it to use it as a tool like Frameworks or IDs
		
		got it got it um another question that I was personally interested in knowing was
		
		what are some generative AI use cases that you think will become mainstream in
		
		the next few years right now we have some indication of where this is headed but uh but you have been in the space
		
		for so long what do you think the major use cases will look like a few
		
		years from now um so one big use case I see is in terms
		
		of like co-piloting um like software developers helping you
		
		writing better faster code um right now but limitation is again
		
		understanding your code base so it's okay if you're like an independent developer who wants to use SK learn
		
		but if you're like in a large Enterprise and you have like thousands of Frameworks and API and micro services
		
		and internal libraries you can't use the model right now so it can't you can't ask the model hey which
		
		internal AWS Library do I use to deploy a new version of I don't know ec2
		
		so so this is like a big gap which we will bridge but then it will really help to make us more efficient and say okay
		
		it's not me that I need to reach through hundreds of GitHub readmates to find the
		
		right library or there's like no documentation at all and I need to read the code to understand is
		
		it relevant or not but this is like outsourced to the AI and we will see new professions
		
		certainly also sound really dubious questionable areas
		
		so a lot of people use AI to automate cold calls and code sales emails say
		
		okay let's say you wanna sell um I don't know app development for
		
		Shopify web shops so before it was you or you
		
		had like a sales agent goes on the website gets the contact data and tries to pitch it and say Hey I want
		
		to sell you this app idea for your shop you want to buy this which gets automated so you get a list like find me
		
		all Shopify stores personalized and email to every store
		
		and then send out the emails so the number of spams was sadly more increase
		
		or the number of like code emails cold calls we get what will sadly increase it's like yeah more personalized
		
		advertisement sales pitches um this was Sally comments yeah downside
		
		which I don't like about the space and then yeah it will third one will be open
		
		up new business opportunities um still early to to say which one and
		
		what I really like is like new applications in gaming so far NPCs are
		
		really stupid it's like you go there um you get an option between like three
		
		answers and then you can choose on this and then you do like a quest a mission
		
		with an NPC and then you go back and say oh have we met I'm David nice to meet
		
		you and you're like yeah I spent the past week with you we killed this massive monster together
		
		and so I think here generative AI can give like a touch of a personalized experience where you have like a
		
		personalized experience with the NPC David who knows what did you do how did you
		
		treat David in the past and then say Oh no I'm not going on a mission again because last time you let you die on
		
		that mission and so so that's like really cool cool application and yeah looking forward to these new
		
		scenarios new ways creative ways to take generative Ai and and yeah uh apply it
		
		to our life yeah uh in fact I was reading about uh generative AI applications for gaming
		
		like you said and it's super interesting how that will evolve because it involves multiple story lines multiple different
		
		characters and that could really benefit with a lot of personalization so totally agree on that and just as a follow-up to
		
		the previous question I'm sure you'd be trying a lot of different AI tools probably things which are still in beta
		
		right now uh any any good uh tools that you have personally found it useful
		
		which are not as popular yet but hopefully will be someday
		
		um
		
		no not not really so so I'm a big fan of Pi torch but that's not a secret
		
		um big fan of fighting phase Transformer ecosystem but that's also not a secret
		
		um yeah vectors so far it's a bit under the radar so so these vectors they
		
		are extremely powerful for a lot of use cases so really I don't know I've been working a lot over the
		
		past five years to educate people on these embeddings and vectors and cool applications you can build and then you
		
		see okay people take some time to get it to think you know like a thousand-dimensional
		
		electric space so human is not really made for this but once you you unlocked it and got the intuition for it
		
		um people use it for really cool stuff so search is one um others like customer aggregation
		
		clustering so we had like um one use case it was from a media company
		
		and in the fashion industry they were interested in like fashion okay what what do teenagers interested in like
		
		which fashion products what's the fashion trend be able to detect fashion trends early
		
		on like what you make up to use which hairstyle to use and and this is like really suitable
		
		with like these amazing approaches where you yeah bring it to a vector space over time and then you see up okay I don't
		
		know a new hairstyle bubbles up and then one goes not crazy into the hairstyle and you have like early adopters then
		
		you can say okay this hairstyle will become like really popular over the next six months this can be like yeah what's
		
		kind of interesting to see and then I say go in and say okay um they did like talk shows and and so
		
		on for for teenagers and adults and say okay let's get this into our talk show and talk about this new fashion trend
		
		um which hairstyle which make up to use and so on
		
		very interesting and uh Niels I also noticed that you spent a lot of time in
		
		research as part of your career uh so if someone were to maybe build out a career in research or
		
		include research as part of their careers uh right now how do you think they should go about it because not many
		
		people uh know about research as as a mainstream profession in that sense
		
		right so how do we how do you how do you recommend people to go about this journey and how has it uh impacted your
		
		career as well if you could maybe share a few thoughts there yeah um so yeah started in research 10
		
		years ago um nowadays sounds a bit funny but my
		
		professor asked me um have a look at neural networks deep learning computer vision people talk
		
		about this again we knew that deep learning or neural networks is a dead
		
		technology it's hopeless it's useless it's not working so so that was like common agreed knowledge for like 20
		
		years and and so figure out why are they talking about like neural networks again
		
		and so that's that's where I started my research career I understand what's neural networks what's deep learning and
		
		will it be relevant why not and yeah as it turns out nowadays everything is deep learning
		
		um so so yeah best way to get into it um is totally try to aim for like a PhD
		
		um to get really the education what doesn't mean to to do
		
		signs so science is of all all about like hypothesis so you have like some
		
		idea um I don't know Simple Thing could be which activation function is the best
		
		for deep learning framework and then you you try to test this hypothesis and say
		
		okay this this is true or this is true or same in search like which which
		
		approach to search works the best um in such and such setting and then you you design the experiments
		
		and yeah machine learning AI this is still a lot about like these
		
		trying arrows so so sadly we don't have a clear way we don't know what is gpt5 how will it
		
		look like um he says so it's a lot of like coming up with hypothesis where we say okay
		
		such type of architecture could work really well how do we test if this is
		
		the case and what extrapolations can we make so you Karma was an idea and 99 of
		
		the case that it fails but what other the learnings you can from this from these failures and then
		
		you extrapolate this to the next idea and so it's really relevant for for machine learning nowadays
		
		and how did how did it impact your career uh because you joined go here now
		
		or do you think it had a major role to play uh in your journey up till now uh
		
		yeah so it had a major role so so when I started
		
		nowadays semantic search is extremely hot popular you have to startups like
		
		bank account and so on who who get like Millions hundreds of millions of investment
		
		because they focus on semantic search um when I've started semantic search as
		
		well as like again no one was working on it didn't work and then so was my research group as post-op we established
		
		yeah we demonstrated like you can use these Transformers to search
		
		and then the vector databases came in and said okay yeah that's that sound interesting it's really promising technology
		
		um so we need to provide the the infrastructure for that because this will take off um over the next years and yeah same my
		
		position actually here let me say okay search as critical role um I was well known in the field for
		
		when I yeah building up the field online so how to use Transformer architectures
		
		to search and yeah that's that's why I got hired because I demonstrated the impact in
		
		science and now we're translating these two foundational models
		
		amazing that's so so great to hear uh Niels as as a last question a lot of
		
		young folks joining in in today's session as well and they'll hopefully kick start their careers in AI uh soon
		
		so any any words of advice or recommendation from your career or
		
		um anything that people should be aware of people should do more yeah
		
		um so in General on multiple things so one
		
		side is like built build products and it's a really good good idea to build
		
		some of these AI enhanced products be it whatever be a text to image text generation text
		
		understanding search just build something out that works um I don't know as a fun project a couple years ago I
		
		built my own email spam classifier because I was annoyed that Gmail is not
		
		filtering out all these code code sales emails so I get like a bunch of people trying to sell me stuff
		
		so I said okay use my knowledge and filter this out and it was like great learning experience and that's I don't
		
		know what what people can do get interested in and build stuff where you learn yeah a lot of pitfalls and
		
		challenges in the field like if you want to really deploy it and second is is continue learning so
		
		there are like many good lectures tutorials blog posts available also textbooks available
		
		um sadly with your people in the field Young Folks all they know is like
		
		Transformers and deep learning um but there's like a lot of Technology
		
		established technology and machine learning that's much simpler much better
		
		so so even such um I don't know I have been using Transformers a lot my spam classifier that I use for my inbox is a
		
		super simple support Vector machine with some features um it's the person in my address book
		
		have a corresponded to that person before like some traditional feature engineering because it was much better
		
		and cheaper and easier than any deep learning Transformer approach so so really learn the basics and then yeah
		
		deep deep in your knowledge and explore different stuff um so so that's that's a good one
		
		fantastic advice that uh I know we are a little over time now but last question
		
		before we let you uh let you go so we uh have a build-a-thon coming up where uh
		
		students of this court will be hacking away for 24 hours straight and will be
		
		building products for generative AI uh any any good ideas on top of your mind
		
		that you would see if people uh build in the building
		
		um no so so yeah I'm a big fan of text
		
		understanding so so right now all the craze is craziness as well like text
		
		generation or before it was like in my generation but text understanding really
		
		yeah it's extremely valuable and it's also cool to build like let's say we did this
		
		Beauty monitoring for like a massive like the biggest TV station in Europe
		
		where they like really plan their program on I'm like okay what are beauty trends of like teenage girls and teenage
		
		boys as I really cool to see how how it goes into life like okay what do they talk
		
		about can we see trans periodic trans so for example in
		
		June there's like the pride months in North America so so each time in June we saw a spike and like okay whatever
		
		um makeup tips for Pride months in North American uh and European summer
		
		they were asking like okay which which makeup has um some protection in it and
		
		and which yeah um but what can people recommend there and you get like a lot of insights in
		
		the in the human Minds to build like these and it's like a cool product at the end to to see where you have like a
		
		visualization at the end and say okay we in the past we use tweets but nowadays
		
		it's a bit hard with the API but or in the past we used Reddit which is also Savvy but hard was uh nowadays was the
		
		changes but yes so you should get these insights um I don't know let's say
		
		generative AI or AI like how did the discourse of AI
		
		change over time when I did take it off and became like really mainstream popular it's like really cool to build
		
		these and get like a really good understanding and it's also highly valuable for for Enterprises so each
		
		Enterprise is highly interested to get an understanding of the customers the competitors their own business the
		
		market where is it going uh what is like the next big thing so what is the next
		
		big social media and if you can I don't know at the end invest in that early
		
		um that's great or if you can invest early into like a video and you know okay I don't know AI is taking off and
		
		it will require a lot of gpus that's also kind of valuable from a
		
		monetary perspective perfect so there you go folks participating in the villaton I hope we
		
		have made your lives a little bit easier now now you have a couple of good ideas to play around with uh but thanks thanks
		
		so much news like I said this was such a complex topic but you explained it so well uh everyone seems to be uh at least
		
		diving into that rabbit hole right now and hopefully they'll uncover more about semantic search in the weeks to come but
		
		thanks for taking your time really really appreciate it uh during the entire session we are a little animated
		
		so people usually screenshot this and post it on social so if you could just do a quick pause it'll help everyone
		
		oh one two just a quick pose with a thumbs up
		
		thumbs up perfect there you go thanks again how was your experience news
		
		yeah great so far so so really good questions uh a lot of Engagement questions coming up so so that's that's
		
		really nice um yeah still I don't know it's cool to have like all these
		
		let's say junior people come and feel extremely motivated and want to hack things together
		
		and I mean in the past we saw really cool applications out of like these these people it's like sometimes more
		
		the more experienced people they are stuck on the same path but then if someone comes in with fresh
		
		fresh eyes fresh Minds says okay this this combination will be really cool and
		
		then okay like a totally amazing product out of that absolutely I think someone in the
		
		comments also mentioned that it's only because of efforts and perseverance of people like Niels that we are seeing the
		
		EI Revolution right now and I totally agree with that so thanks for all your hard work over the over the last decade
		
		and longer for everything that you have done so far and will continue to do so we are super excited to see everything
		
		that you build next and thanks again for joining us right thank you bye bye everyone
		
		bye
		
		folks so that was a fantastic session uh by Niels
		
		um totally loved the love the entire session uh with demos examples and
		
		everything I hope everyone uh were able to yeah amazing session totally agree
		
		that everyone was able to follow through and this was the second last session so
		
		by now obviously I'm assuming that you would have gone through all the previous sessions and leading up to this session
		
		you would be much better equipped to understand everything that was uh taught by Niels right so thanks again for uh
		
		joining I'll just quickly share my screen and talk about what's coming up
		
		next in the cohort right so we have uh the final session and rapper party uh on
		
		Saturday with Saiyan from H2O so this will be the last session in the series
		
		but uh definitely will be worth your time so we'll wrap up the entire cohort
		
		this Saturday day and of course they'll be building on uh happening next weekend so perfect way to sum up the entire
		
		entire experience and obviously housekeeping by now your folks must be
		
		aware about so I won't spend too much time here but make sure that how you have done all of this uh to gain the
		
		best experience of the cohort and my son to Milestones to graduate I know a lot
		
		of you folks have been asking about this uh earlier but the only Milestones that
		
		you need to complete and the series of certificate is attend all the live sessions and post your learnings after every session on LinkedIn and Twitter
		
		using the right hashtags and tag us tag the speakers so that they will also be able to see your learnings right so make
		
		sure you do that and apart from that uh obviously the build-a-thon is coming up so if you haven't submitted your ideas
		
		yet uh this is the best time to do so because today is the last
		
		has posted the link here in the chat so you'll be able to check it out I also
		
		have something fun to show you something that we have uh just recently uh
		
		launched in fact not even launched but just a small sneak peek uh so let me know when you can
		
		see my screen I'll also [Music]
		
		I'll quickly share my screen and
		
		can you please give a quick thumbs up reaction uh so that
		
		yeah I see a lot of Thumbs Up reaction so here you go quick sneak peek tanma will also share the link to this so that
		
		you can check it out on Twitter and Linkedin but here we go
		
		[Applause]
		
		yes so this is something new that's coming out from the front folks uh for
		
		folks uh who have been here till the end I thought it will be good to give you a small sneak peek before we let you go so
		
		uh we'll be launching it super soon but uh until then here's a small teaser to
		
		keep you excited and yes as always thanks so thanks so much for joining uh
		
		if it's uh if there are any questions please put it in the chat I'm here for two more minutes so you can answer your
		
		queries uh I saw some questions about the build-a-thon in the Q a tab uh about
		
		people being participate people can people participate from outside of Bangalore but folks this is an offline
		
		uh build-a-thon so you won't be able to participate from elsewhere you need to be present in Bangalore
		
		for participating but uh apart from that any other questions how will we get
		
		swags so all you need to do for so access of course uh just post your learnings and submit your ideas for the
		
		build-a-thon will reach out to you we have already sent it to some of the members of the cohort but
		
		you'll hear from us once you uh once you are shortlisted for that how to get open
		
		AI credits you have already sent out communication to everyone who has submitted ideas so please make sure you
		
		check your emails or we have also sent out WhatsApp messages so you can Avail the open EI credits make sure that you
		
		sign up there because we'll only be able to give our credits to people who submit it within the deadline uh right not yet
		
		received please reach out to someone from our team and they'll be able to help you out but if you have submitted
		
		your idea uh I'm pretty sure you would have received a form by now uh right
		
		and uh just for the certificate uh fill up some will send out instructions for this uh
		
		in the last session which is happening on 20 seconds so please don't worry about it uh but yeah you know the
		
		eligibility criteria you need to attend all the live sessions and post your learnings so just make sure you do that
		
		and everything else will be taken care of by our team as always
		
		Twitter link Twitter handling the links for this teaser as well go check it out uh wish I could attend the hackathon but
		
		can't we'll try live streaming the demos so that you can irrespective of where you are Journey from you'll be able to
		
		watch the uh what's the live stream at least and maybe participate next time
		
		but uh how many ideas submission submitted till now and how many would be
		
		selected we'll be sending out the final final shortlist uh within the next few
		
		days itself our team is still in the process of shortlisting the best ideas uh but in terms of number of ideas
		
		I think there are hundreds of different uh ideas being submitted um and some of them are really good uh I
		
		had a chance to glance for them last night and it's pretty amazing what everyone has come up with uh but uh but
		
		yeah please if you haven't submitted yet and but if you want to participate in the hackathon make sure that you do it
		
		right away after this after this live stream right and uh and yeah any more questions any
		
		any other questions or anything else that I can help with let me know if not we'll wrap this up uh we have a last
		
		session coming up on 20 seconds so make sure that you join in for that one as well it'll be super fun
		
		then what is the next card of tpf give us suggestions let us know what you want
		
		to see from us uh AI is something that the community uh told that they'd be
		
		interested in learning so we came up with this let us know what uh what we
		
		should do next and we'll definitely make sure that we take it into consideration and come up with that do something for
		
		beginners or literally most of our cohorts are for beginners so so don't
		
		worry about it it will be beginner friendly uh blockchain we have the product house
		
		Community for it so go check out the product house uh if you are interested in blockchain or web3
		
		PM Fellowship we already have something like this no code to stop product management we have already done a CBC
		
		around this uh in the past so product marketing very interesting
		
		will definitely you'll definitely see something for product marketing from DPF
		
		soon psychology in Tech wow super interesting
		
		product portfolio challenge check out teardowns check out our product teardowns that we do every month uh
		
		that's pretty equivalent to forming a product portfolio of sorts uh does product house have blockchain cohorts
		
		yes we did our three fundamentals cohort last year the recordings are also available on the academy so go check it
		
		out the product.house uh how to know about upcoming cohort's best way to be updated is uh sign of a
		
		newsletter follow us on all our social platforms that's where we uh that's why
		
		we post all our updates and along with that obviously a lot of knowledge and content that will
		
		um that will help you out how can we support tpf uh the easiest way is to uh
		
		obviously attending these sessions uh volunteering for the community it's an
		
		entirely volunteer um committee so you can volunteer with tpf as well but yeah
		
		just showing us enough love uh for everything that we do is is something
		
		that we can that you can do without without any major effort right so how to
		
		volunteer I think we have a volunteering firm that we had sent out a couple of days back but if you are on our slack
		
		we'll send it out again so make sure that you join us like I will send out the volunteering form again which you
		
		can fill and our team will reach out to you
		
		awesome I don't see any more questions uh so we'll probably wrap this up uh but
		
		I am super excited for the last session and I definitely hope
		
		you're pretty excited for it as well and I hope you like this session make sure
		
		that you post your learnings as notes on LinkedIn and Twitter um always always excited to read them uh
		
		after this session so make sure you do that and yeah thanks thanks for joining again
		
		good night see you super soon uh if you are in Bangalore for the build-a-thon uh
		
		looking forward to meet you as well but if not see you online during the next