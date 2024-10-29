

project level updates(past quarter)

1.Semantic Search 
- Corpus delivery done multiple times. Not updated certain times because of multiple issues. Automation pipeline broke, waited on catalog for 1.5 months. Now in stable state.
	- Delta implementation: 90% of delta pipeline is done. Facing issues in last 10% of delta pipeline. To be completed this week. Delta pipeline without optimisation takes 2 hrs to run currently. 
- Fashion dictionary developed and throughly tested. To be integrated into main corpus this week/next week.
- Autosuggest: Main portion developed by March. Improved over small iterations in past few months. Ajio not in a position to consume it. Higher priority on other projects for the next 6 months. Dashboard developed as well for demo of autosuggest. 
- Contextual spell correction(autocorrect): Developed working version, with demo dashboard. Developed to counter CoE's alternative modules for initial stages of search pipeline , mainly for stemming queries before using Couture corpus for better search results. 
	- To work on improving latency without relying on prod servers deployment for now. Parallel process for deployment of pipelines on Ajio prod servers discussions are ongoing. Kritika also on board with running our usecases on prod servers.  
- Widgets- 
	- query substitution -- initially worked on from March, deferred then due to lower priority. Picked up again in August, with this being actively being pursued by search team in 6 month AOP roadmap for couture. 
	- alternate brand/entity -- A version of output ready. To migrate Meghana onto this project for refinement. 


2.Similar product recommendation: 
- Started A/B in April. Restarted after a Ajio side fix in early June. Won A/B by August, went 100% live on Android and IOS on 25th Aug. RRA requested for another A/B with their new output. To start after moratorium. 
- Worked on implementing LTR and finetuned transformers. 
- Worked on Reranking for better metrics. 

3.Relevancy: 
- Have been ready for A/B since start of year. Developed cold start problem fixes in the meantime and Fixed issues along with Ajio team in output consumption. 
- Blocked on Ajio fixing a bug in their backend. 
- Precision only being handled by Ajio upto 4 digits. Ajio working on increasing precision to 10 digits, for providing accurate ranking for 13L products.
- Precision improvement and Ajio side bug-fix to go in post current sale. 

4.Demand forecasting: 
- Started from scratch on new requirement of sku level predictions from June ending onwards.
	- tried different model(Fourier transform, LNN's, trees, etc) for best possible outputs. 
	- Iterations of different features experimented with. 
- Weekly iterations of frontend done for demo according to new requirements.
- Backtesting of Couture model done
- most recent status: 
	- Gave demo to a large set of audience which included Reliance retail, Ajio online, Reliance offline(centro, trends), Jio mart members. 
	- Assortment planning to be picked up for reliance stores and pharma
	- To have a comparison of sample output against SAP F&R. 
	- In process of taking Demand forecasting live for VMS on prod servers.

5.Widgets
-  platform widgets : Developed by Jan, Went into A/B 2 months back. 2 widgets live.
- User level widgets: Developed from Couture end. Ajio not ready for User level widgets consumption


Projects kept under backburner: 
- pricing : Gross margin 
- fraud detection
- return reduction: size



A/B results: 

completed in past year: 
B2B A/B
B2C similars A/B
Platform level widgets A/B
Search A/B


in progress: PLP A/B(yet to start)

