


# mermaid trials

2022-08-13
15:08



### gantt chart

```mermaid
gantt
    title A Gantt Diagram
    dateFormat  YYYY-MM-DD
    section Section
    A task           :a1, 2014-01-01, 30d
    Another task     :after a1  , 20d
    section Another
    Task in sec      :2014-01-12  , 12d
    another task      : 24d
```

### graph

```mermaid
graph TD
	topic name: 
```


```mermaid
%% https://mermaid-js.github.io/mermaid/#/classDiagram
 classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
```

[mermaid live editor](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbiAgQVtDaHJpc3RtYXNdIC0tPnxHZXQgbW9uZXl8IEIoR28gc2hvcHBpbmcpXG4gIEIgLS0-IEN7TGV0IG1lIHRoaW5rfVxuICBDIC0tPnxPbmV8IERbTGFwdG9wXVxuICBDIC0tPnxUd298IEVbaVBob25lXVxuICBDIC0tPnxUaHJlZXwgRltmYTpmYS1jYXIgQ2FyXVxuXHRcdCIsIm1lcm1haWQiOnsidGhlbWUiOiJkZWZhdWx0In19)

```mermaid
graph LR
	%%==============%%
	%% Declarations %%
	%%==============%%
		A[portfolio management]
		B[text]	
		C[text]
	%%=========%%
	%% Linking %%
	%%=========%%
	%% comment
	A --> B & C
	
	%% subgraph
	%% end
class A,B,C internal-link;
style A fill:#EBDBB2,stroke:#EEE,stroke-width:4px,color:#FFF
```

[mermaid live editor](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbiAgQVtDaHJpc3RtYXNdIC0tPnxHZXQgbW9uZXl8IEIoR28gc2hvcHBpbmcpXG4gIEIgLS0-IEN7TGV0IG1lIHRoaW5rfVxuICBDIC0tPnxPbmV8IERbTGFwdG9wXVxuICBDIC0tPnxUd298IEVbaVBob25lXVxuICBDIC0tPnxUaHJlZXwgRltmYTpmYS1jYXIgQ2FyXVxuXHRcdCIsIm1lcm1haWQiOnsidGhlbWUiOiJkZWZhdWx0In19)


- mermaid chart with changing fonts: 
```mermaid
graph TD
start[<font size=1>a]-->a1[<font size=6>1.发票检验]
a1-->b1[<font size=6>发票税号正确]
b1--<font size=6>是-->c1[<font size=6>发票下方盖公司有效印章]
c1-->d1[<font size=6>发票背面填写项目]
d1-->e1[<font size=6>项目名称]
d1-->e2[<font size=6>项目负责人签名]
d1-->e3[<font size=6>报销人签名]
d1-->e4[<font size=6>审核人签名]
start-->a2[<font size=6>2.填写报销单]
a2-->b2[<font size=6>项目负责人审核通过]

```



mermaid with large flowchart: 
```mermaid
graph TD 
	sq[<font size=0.1>Square shape] --> ci((Circle shape)) 
	subgraph A 
		od><font size=0.1>Odd shape]-- <font size=0.1>Two line<br/>edge comment --> ro 
		di{<font size=0.1>Diamond with <br/> line break} -.-> ro(<font size=0.1>Rounded<br>square<br>shape) 
		di==>ro2(<font size=0.1>Rounded square shape) 
	end 
	%% Notice that no text in shape are added here instead that is appended further down 
	e((Inner / <font size=0.1>circle<br>and some odd <br>special characters)) --> od3><font size=0.1>Really long text with linebreak<br>in an Odd shape] 
	
	%% Comments after double percent signs 
	e((Inner / <font size=0.1>circle<br>and some odd <br>special characters)) --> f(<font size=0.1>,.?!+-*ز) 
	cyr[<font size=0.1>Cyrillic]-->cyr2((<font size=0.1>Circle shape )); 
	
	
```



```mermaid
graph LR
	%% Class Definitions
	%% =================
	
	classDef FixFont font-size:11.5px;
	
	%% Nodes
	%% =====
	
	A[CREATIVITY]:::FixFont --> B[Combinatorial]:::FixFont;
	A[CREATIVITY]:::FixFont --> C[Exploratory]:::FixFont;
	A[CREATIVITY]:::FixFont --> D[Transformational]:::FixFont;
	B[Combinatorial] --> E[Problem-driven]:::FixFont;
	B[Combinatorial] --> F[Similarity-driven]:::FixFont;
	B[Combinatorial] --> G[Inspiration-driven]:::FixFont;
	G-->H[next step]:::FixFont;
	F-->H[next step]:::FixFont;
	H-->y(output)
	y-->i(adding one stage)
	i-->j(adding 2nd extra stage)
	
	
	%% Node styles
	%% ===========
	
	style A fill:gold;  
	style B fill:cyan;
	style C fill:cyan;
	style D fill:cyan;
	style E fill:mediumvioletred;
	style F fill:mediumvioletred;
	style G fill:mediumvioletred;
```

[![](https://i.imgur.com/xX1HyYBt.png)](https://i.imgur.com/xX1HyYB.png)
