# History of Artificial Intelligence  

**Artificial Intelligence (AI)** is a branch of computer science that deals with creating  
computer systems capable of performing tasks that usually require human  
intelligence. Such tasks include:  

- Image and speech recognition  
- Decision-making under uncertainty  
- Language translation  
- Problem solving and planning  

> 💡 **Key concept:** *AI is not a single specific algorithm, but a set of methods  
> and techniques that enable machines to "think" or at least imitate  
> human cognitive functions.*  

AI is no longer considered just a theoretical concept, but a fundamental technology  
that is changing healthcare, finance, transportation, education, and entertainment. AI is not  
"magic" – it is mathematical models, data, and computing power that together create useful tools.  


## Early Foundations (1940s – 1950s)  

### Key figures and ideas  

**Alan Turing** (British mathematician): In 1950 he published the paper *„Computing Machinery and Intelligence"*,  
in which he asked the question *„Can machines think?"*. He proposed the **Turing test** – if a machine can hold  
a conversation that a human cannot distinguish from a human one, it may be considered intelligent.  
**Turing machine**: A theoretical model of computation that laid the mathematical foundations for all modern computers.  

---  

## Dartmouth Conference (1956) – The Birth of AI  

If we had to pick a single moment when artificial intelligence was „born" as a  
scientific discipline, it would be the **summer of 1956 at Dartmouth College** in Hanover,  
New Hampshire, USA. The conference that took place there gave the world not only a new  
research direction – it also gave it the very term by which we know it today.  


![Dartmouth Conference](../data/darth-conf.png)


### How it came about  

In the summer of **1955**, John McCarthy (then a 27-year-old mathematician at Dartmouth College)  
together with Marvin Minsky, Nathaniel Rochester, and Claude Shannon wrote  
a grant application to the Rockefeller Foundation. In this document, for the first time  
they used the phrase in writing:  

> *„artificial intelligence"*  

The proposal described a plan for a two-month workshop for about 10 scientists who would  
jointly investigate whether aspects of human intelligence could be described so precisely  
that a machine could simulate them. The Rockefeller Foundation approved the grant –  
in the amount of **$13,500**.  

### Participants: the „founding fathers" of AI  

A total of **10 scientists** took part in the conference – at various times  
throughout the summer of 1956. Many of them later became legends of the field:  

| Name | Institution | Later contribution |  
| :--- | :--- | :--- |  
| **John McCarthy** | Dartmouth College | Founder of LISP, coined the term „AI", Turing Award 1971 |  
| **Marvin Minsky** | Harvard University | Founder of MIT AI Lab, Turing Award 1969 |  
| **Claude Shannon** | Bell Labs | Founder of information theory |  
| **Nathaniel Rochester** | IBM | First programmer on the IBM 701 |  
| **Allen Newell** | RAND Corporation | Co-author of Logic Theorist and GPS |  
| **Herbert Simon** | Carnegie Tech | Nobel Prize in Economics 1978, Turing Award 1975 |  
| **Arthur Samuel** | IBM | Pioneer of machine learning (checkers program) |  
| **Oliver Selfridge** | MIT Lincoln Lab | Pioneer of pattern recognition |  
| **Ray Solomonoff** | | Founder of algorithmic probability theory |  
| **Trenchard More** | Princeton | Researcher in symbolic logic |  

> 🎓 **For students:** The list of participants shows that from the very beginning AI was  
> not just „coding" – it was an interdisciplinary science at the intersection of mathematics,  
> psychology, linguistics, and engineering.  

### The main hypothesis of the conference  

The central idea that McCarthy formulated in the proposal and that became  
the fundamental assumption of the entire field:  

> *„Every aspect of learning or any other feature of intelligence can in  
> principle be so precisely described that a machine can be made to simulate it."*  

This is a bold – and still debated – hypothesis. It assumes that **human  
intelligence is algorithmically reproducible**. It was precisely this assumption that was  
fertile ground for the following decades of research: for the triumphs, as well as for  
disappointments and AI winters.  

> In the early 1960s, McCarthy argued that 'computation may someday be organized as a public utility'.


### What actually happened at the conference  

The conference was not a grand event. It was an informal summer  
workshop where scientists met in groups, discussed, and presented  
their work. The atmosphere was more like an academic brainstorming session than a formal  
conference.  

The most significant thing shown there was the **Logic Theorist** program  
by Newell and Simon – the first program that proved mathematical theorems from  
Bertrand Russell's Principia Mathematica. When Newell presented it,  
it was the first real proof that a computer could perform „intelligent" activity.  

Paradoxically, the participants **did not know about each other's projects** – each  
worked on their own approach (symbolic logic, neural networks, language  
models). This divergence foreshadowed from the very beginning that AI would not be a single  
method, but a set of different directions.  

### Legacy: Why Dartmouth still matters today  

1. **Terminology:** The term *„artificial intelligence"* became the international  
   standard. McCarthy chose it deliberately – it distinguished it from the then-current  
   research in cybernetics (Wiener) and automata theory, which had different connotations.  

2. **Legitimacy:** The conference gave AI the status of an academic discipline. After  
   Dartmouth, AI is something that is taught, funded, and researched systematically.  

3. **Community:** Dartmouth brought together scientists from different institutions who  
   built networks, collaborated, and founded laboratories. The AI Lab at MIT  
   (Minsky + McCarthy, 1959) and the AI Lab at Stanford (McCarthy, 1963) grew directly  
   out of this community.  

4. **Optimism – and its price:** Scientists left the conference full of optimism.  
   Simon predicted that „within 10 years a computer will be the world chess champion"  
   and „within 20 years it will be able to do any work a human does." This  
   optimism attracted funding, but also disappointment when the visions were not fulfilled  
   in the expected time – which directly led to the first AI winter.  

> 💡 **Conclusion:** Dartmouth 1956 was not just an academic milestone – it was the moment when  
> humanity collectively decided for the first time that creating artificial intelligence is  
> a legitimate scientific goal, not just a sci-fi fantasy.  

---  

### Early approaches: Symbolic AI (GOFAI)  

> 🎓 **For students:** Symbolic AI assumed that human thinking could be reduced to manipulating  
> symbols according to fixed rules – similar to logic or mathematics.  

- **Logic Theorist** (1956, Newell & Simon): The first program that proved mathematical theorems  
- **Samuel's checkers program** (1952): Learned to play through self-play – an early example of **machine learning**  
- **LISP** (1958, McCarthy): A programming language designed specifically for AI research  

> ⚠️ **Limitations of early systems:** They worked only in very narrow domains and required manual  
> encoding of knowledge.  


## Key Milestones (1960s – 1990s)  

### First interactive systems  

- **ELIZA** (1966, Weizenbaum): A simple chatbot that simulated a therapist using pattern matching and word substitution.  

> 🤔 **Discussion question:** Why do people sometimes attribute „understanding" to simple systems like ELIZA?  


https://www.youtube.com/watch?v=B6rKUf9DWRI  

```  
### The Mother of All Demos (1968)  

In 1968, Douglas Engelbart presented a revolutionary demonstration of computer technologies that were decades  
ahead of their time. He demonstrated the first computer mouse, text editing similar to today's text editors,  
hypertext links reminiscent of the future internet, as well as remote collaboration and video communication.  
The video shows how Engelbart imagined the future of working with computers – interactive, interconnected, and focused  
on sharing information. Today, this presentation is considered one of the most important moments  
in the history of computing.  
```  


```  
The 1960s were a period when the world seemed to suddenly awaken to an era of technology, creativity, and  
bold visions. In computing, the first interactive computers were born, the foundations of the internet were laid,  
and scientists began experimenting with ideas that we now take for granted. In parallel with this,  
the space program was pushing the boundaries of human capability, and culture was undergoing radical  
changes – from music through design to the way people thought about the future. It was a decade  
in which technology, science, and social movements merged into one great acceleration. It was precisely in this  
environment that Engelbart's demonstration was created – as proof that imagination and courage can outpace  
their time by whole decades.  

From today's perspective, it seems that it was precisely in this decade that the invisible but crucial foundations of today's  
digital age and artificial intelligence were laid. In laboratories, the first neural networks and perceptrons were created, which,  
although they did not yet reach today's performance, defined the direction of the entire field for the next 60 years.  
J. C. R. Licklider at that time dreamed of an „intergalactic computer network", which was a direct precursor of today's  
internet, and the concept of time-sharing allowed people to interact with computers in real time instead of waiting for  
results from the previous day. This unique combination of bold theories, state-funded research, and  
practical experiments created fertile ground that we still draw on today. Without the optimism and research investments  
of the 1960s, we would not have the computers that surround us today, let alone the intelligent systems that  
help us solve complex problems.  
```  

  

### Expert systems (1970s – 1980s)  

> 🎓 **Definition:** Expert systems are AI programs that imitate the decision-making of human experts  
> using rules of the type *„if – then"*.  

| System | Field | Significance |  
|--------|--------|---------|  
| **DENDRAL** (1965–69) | Chemistry | Helped identify molecular structures |  
| **MYCIN** (1972) | Medicine | Diagnosed blood infections and recommended antibiotics |  
| **XCON** (1980) | IT configuration | Saved the company DEC millions of dollars |  

> 💡 **Lesson:** Expert systems were successful, but difficult to maintain and unable  
> to learn from new experiences.  

### The return of neural networks and machine learning  

- **Backpropagation** (1980s): An algorithm for training multilayer neural  
  networks (Rumelhart, Hinton, Williams)  
- **Convolutional neural networks (CNNs)** (Yann LeCun): Enabled handwriting recognition directly from data  
- **Deep Blue vs. Kasparov** (1997): IBM defeated the world chess champion – a demonstration of the power  
  of combining raw computing power with heuristics  

> 🎯 **For students:** This development showed that approaches based on data and learning can  
> outperform systems based exclusively on manually coded rules.  


## "AI Winters" – Periods of Declining Interest (1970s and 1990s)  

### What are "AI winters"?  
> 🎓 **Definition:** Periods when there was a significant reduction in funding and interest in AI research  
> due to unmet expectations.  

### The first AI winter (1970s)  
- Causes:  
  - Overly optimistic predictions („human-level intelligence within 20 years")  
  - Limitations of symbolic AI: missing „common sense", inability to handle real complexity  
  - Insufficient computing power  
- **The Lighthill Report** (1973): Criticism of AI research in the UK → funding cuts  

### The second AI winter (late 1980s – early 1990s)  
- Collapse of the expert systems market:  
  - High maintenance demands  
  - Inability to learn from new experiences  
  - Bankruptcy of specialized hardware companies (LISP machines)  
  
- The term "AI" became stigmatized → researchers renamed their work to  
  *„machine learning"*, *„neural networks"*  

> 💡 **Lesson for the future:**  
> - It is important to manage expectations realistically  
> - Practical applications and measurable results are key to maintaining support  
> - Technological limitations must be taken seriously  

---  

## The Modern Era (2000 – 2010): The Return of AI  

### Three pillar factors of the AI renaissance:  
1. **Computing power**: GPUs (graphics processing units) enabled parallel training of large neural networks  
2. **Big Data**: The internet, social networks, and sensors generate enormous amounts of training data  
3. **Algorithmic breakthroughs**: Deep learning and architectures like Transformers  

### Key moments:  
- **ImageNet** (2009): A dataset of millions of labeled images → catalyst for computer vision  
- **AlexNet** (2012): A deep convolutional network that decisively won the ImageNet competition → the start of the deep learning era  
- **AlphaGo** (2016): Defeated the world champion in Go – a game considered too complex for AI  
- **Open-source frameworks**: TensorFlow (2015), PyTorch (2016) → democratization of access to AI  

> 🎯 **For students:** Modern AI is not about „programming rules", but about **training models on data**.  
> The quality and quantity of data are often more important than the complexity of the algorithm.  


## Large Language Models (LLMs) – The Current Revolution  

### What are LLMs?  

> 🎓 **Definition:** Large Language Models are neural networks trained on enormous amounts  
> of text that can generate and understand human language.  

### Key technologies:  
- **Transformers** (2017, Google): An architecture based on *self-attention* mechanisms → more efficient processing of long texts  
- **BERT** (2018): A model that learns context bidirectionally → improved results in many NLP tasks  
- **GPT series** (OpenAI): Showed the power of scaling – larger models + more data = better capabilities  

### What can LLMs do?  
✅ Write essays, answer questions, summarize texts  
✅ Translate languages, generate code, hold conversations  
✅ Help with teaching, research, and creative work  

> ⚠️ **Limitations and risks:**  
> - They can generate incorrect or misleading information („hallucinations")  
> - They can amplify biases present in the training data  
> - They require enormous computing resources → environmental and economic questions  

> 🤔 **Discussion question:** How should we use LLMs in education to support learning, not just copying answers?  

---  

## When Sci-Fi Was Ahead of Its Time: Ideas from Movies That Are Reality Today  

For decades, sci-fi movies have shown us the world of the future – some  
inventions looked like pure fantasy, others gradually became a common part  
of our lives. The 1960s were a period when the world seemed to awaken to an era  
of technology and bold visions, but only today do we see how many of these dreams  
came true. Science fiction often served as a „testing ground" for future  
innovations. Here are a few examples of technologies that once existed only on  
the screen, and today we use them almost every day.  

---  

**Communicating with a computer in natural language**  
In the movie *Alien* (1979), the crew of the Nostromo communicates with the ship's  
computer MOTHER using voice commands.  
🔗 **Scene clip:** [Alien (1979) – Dallas Accesses Mother](https://www.youtube.com/watch?v=oxdCEBppRM8)  

Today, virtual assistants like Siri, Google Assistant, or large language  
models (ChatGPT, DeepSeek) are a matter of course – we talk to them, ask them about  
the weather, dictate messages, or use them as creative partners for  
solving complex problems.  

---  

**Video calls and teleconferencing**  
In *Aliens* (1986), Lieutenant Ripley calls her superiors through  
a screen while in hyperspace. At the time, this was a futuristic luxury.  
🔗 **Scene clip:** [Aliens (1986) – Ripley Video Call Scene](https://www.youtube.com/watch?v=qSSRXuHfAwY)  

Today, millions of people use video calls via Zoom, Teams, or FaceTime for  
work, education, and private meetings, which became the standard especially after  
2020.  

---  

**Holographic displays and telepresence**  
We admired holograms floating in the air in the original *Star Wars*  
(1977) or in *Blade Runner* (1982).  
🔗 **Scene clip (Star Wars):** [Star Wars (1977) – Princess Leia Hologram](https://www.youtube.com/watch?v=8N_Cj3ZS9-A)  

Although we don't yet have full 3D projections in the air at home, in the real world  
holographic display cases, stage effects, and advanced head-up displays already exist in  
cars and airplanes. Technologies like Microsoft HoloLens, in turn, enable the feeling  
of „being there" from a distance.  

---  

**Tablets and touchscreens**  
The *Star Trek* crew used the „PADD" back in the 1960s. *2001: A Space Odyssey*  
(1968) showed journalists with flat screens.  
🔗 **Scene clip (2001):** [2001: A Space Odyssey (1968) – Tablet Scene](https://www.youtube.com/watch?v=5T1UGfm_OMM)  

The real boom came only with the iPad (2010) and subsequent tablets, which today  
we find in schools, hospitals, and in the hands of small children.  

---  

**Artificial intelligence as a companion**  
The movie *Her* (2013) introduced an operating system (AI) that the main character  
falls in love with.  
🔗 **Scene clip:** [Her (2013) – Installing Samantha OS](https://www.youtube.com/watch?v=f9Hg1x-Ctlw)  

Today we don't have AI with full emotional intelligence yet, but language models are  
at such a level that we have natural conversations with them and use them as  
creative partners.  

---  

**Autonomous cars**  
In the movie *Total Recall* (1990), the car was driven by „Johnnycab" – a robotic taxi without  
a driver. *I, Robot* (2004) showed self-driving cars in regular traffic.  
🔗 **Scene clip (Total Recall):** [Total Recall (1990) – Johnnycab Scene](https://www.youtube.com/watch?v=679i0AGxXFk)  
🔗 **Scene clip (I, Robot):** [I, Robot (2004) – Autonomous Car Scene](https://www.youtube.com/watch?v=EZKNush8qsI)  

Today, fully autonomous taxis (Waymo) already drive in some cities of the world, and  
advanced driver-assistance systems are standard in new cars.  

---  

**Universal translators**  
*The Hitchhiker's Guide to the Galaxy* and *Star Trek* gave us a universal translator  
that instantly interprets a foreign language.  
🔗 **Scene clip (Star Trek):** [Star Trek – Universal Translator Scene](https://www.youtube.com/watch?v=5oQ0FbtbQQU)  

Today, apps like Google Translate enable instant translation of spoken words  
through headphones and camera in real time, breaking down language barriers.  

---  

**Unmanned aerial vehicles (drones)**  
In the movie *Minority Report* (2002), small drones flew around scanning people's  
faces.  
🔗 **Scene clip:** [Minority Report (2002) – Spider Drone Scene](https://www.youtube.com/watch?v=EQ55c87m4_4)  

Today, drones are commercially available for filming, package delivery, or  
agricultural monitoring.  

---  

**Touchless gesture control**  
In the movie *Minority Report* (2002), the main character controlled an interface using  
hand movements in space.  
🔗 **Scene clip:** [Minority Report (2002) – Gesture Interface](https://www.youtube.com/watch?v=33Raqx9sFbo)  

Today, this technology is used by virtual reality (VR) systems and some  
modern cars that react to the driver's gestures.  

---  

**3D printing (replicating objects)**  
In the series *Star Trek*, a „replicator" was used that could create food  
or objects on demand.  
🔗 **Scene clip:** [Star Trek TNG – Replicator Scene](https://www.youtube.com/watch?v=8kw9_O10Fh8)  

Although we are not yet at the level of molecular synthesis, 3D printing today already allows  
us to produce functional parts, prosthetics, and even building components.  

---  

**Payment cards and cashless transactions**  
In *Star Trek*, classic money no longer existed – the world had moved to a digital  
economy and credit chips.  
🔗 **Scene clip (Star Trek IV):** [Star Trek IV – "They don't use money"](https://www.youtube.com/watch?v=XQQYbKT_rMg)  

Today, cashless transactions are the standard, with payment cards,  
smartphones, or cryptocurrencies having moved the idea of digital money into everyday  
reality.  


---  

### When Sci-Fi Was Ahead of Its Time: European and Russian Predictions  

That's a great question! While Hollywood dominates blockbusters, European and Russian  
cinema often brought deep philosophical visions that predicted  
not only technologies, but also their social impact.  

Here are a few fascinating examples of „predictions" from these regions:  

---  

### Germany: Metropolis (1927) and Frau im Mond (1929)  

German expressionism laid the foundations of the sci-fi visual style, to which we owe  
more than we think.  

* **Humanoid robots (Metropolis):** The character „Maschinenmensch" (machine  
  human) was the first iconic robot on screen. It inspired not only C-3PO from  
  Star Wars, but predicted today's humanoids like **Optimus from Tesla**  
  or the robots from **Boston Dynamics**.  

* **Countdown before the rocket launch (Frau im Mond):** Director Fritz Lang  
  needed to create tension before the rocket launch, so he invented the countdown  
  „3, 2, 1... LIFTOFF!". Nothing like that existed before this movie. **NASA** later  
  adopted this dramatic element as a standard technical procedure.  

* **Video phone (Metropolis):** In the movie, we see a video call device as early as  
  1927 – almost 100 years before **Zoom** became our daily routine.  
  
---  

### Czechia: Ikarie XB-1 (1963) and R.U.R. (1920/1938)  

Czechoslovak cinema and literature gave the world the very foundation of robotics.  

* **The word „Robot" (R.U.R.):** Although it is a play by Karel Čapek (later  
  filmed), it is here that the term robot originated. Čapek's robots were not made of  
  screws, but were **biological entities** – what today we call **synthetic biology**  
  or bioengineering.  

* **Space station design (Ikarie XB-1):** This film (a precursor to Lem's  
  *Solaris*) showed life in space as sterile, modern, and minimalist.  
  It predicted **automatic doors**, intercoms, and onboard communication  
  systems that the American Star Trek later „copied".  

---  

### France: Alphaville (1965) and A Trip to the Moon (1902)  

The French have always focused on the connection between technology and the state.  

* **An all-powerful AI ruling a city (Alphaville):** The computer Alpha 60 controls the entire  
  city, forbids emotions, and optimizes the lives of citizens based on logic. It is  
  a chilling prediction of today's **Smart Cities** and social credit algorithms,  
  which use **Big Data** to predict and influence people's behavior.  

* **Space tourism (A Trip to the Moon):** Georges Méliès showed a trip to the Moon  
  at a time when cars were a rarity. Today, thanks to companies like **SpaceX** or  
  **Blue Origin**, the vision of space tourism is becoming a commercial reality.  

---  

### Russia / USSR: Amphibian Man (1962) and Aelita (1924)  

Soviet sci-fi often looked at the limits of human capability and the transformation of the body.  

* **Artificial organs and bio-hacking (Amphibian Man – Chelovek-amfibiya):** A film about a man  
  with transplanted shark gills predicted the era of **advanced  
  transplant surgery** and experiments with liquid breathing  
  (perfluorocarbons), which today are being researched for extreme deep-sea diving  
  or medicine for premature babies.  

* **Constructivist aesthetics of technology (Aelita):** This silent film showed  
  futuristic Martian costumes and machines that were ahead of their time in terms of  
  **geometric design of utilitarian objects**, which we see today in modern  
  industrial design.  
  

---  

The list could go on. It is fascinating that many sci-fi creators  
were not just visionaries, but often directly inspired engineers to actually  
build these technologies. Today we live in an era that once  
only they imagined.  


## The Future of AI – Challenges and Opportunities  

### Technological trends  

- **Multimodal models**: Processing text, images, audio, and video simultaneously (e.g., GPT-4, Gemini)  
- **More efficient models**: Efforts to reduce computational demands and energy footprint  
- **AI for science**: Help with drug discovery, climate modeling, space analysis  

### Ethical and social challenges  

> How can we ensure that AI systems are fair and unbiased?  
> Who is responsible when AI makes a mistake?  
> How to protect privacy in the era of massive data analysis?  
> How to prepare the workforce for the changes caused by automation?  

### Artificial General Intelligence (AGI)  

> 🎓 **Definition:** AGI is a hypothetical AI with human-level intelligence in all  
> areas – not just in narrow tasks.  

- Current status: Most experts consider AGI to be distant (decades away), but not impossible  
- Important: Research on **AI safety and alignment** – how to ensure that powerful  
  AI systems follow human values  


## Chapter Summary  

✅ AI has a long history full of optimism, disappointments, and breakthroughs  
✅ The modern success of AI rests on three pillars: **data, computing power, algorithms**  
✅ LLMs represent the current revolution, but also bring new challenges  
✅ AI is already changing almost every industry – from medicine to art  
✅ The future of AI depends not only on technologies, but also on **ethical decisions and regulation**  

## Questions and Discussion  
