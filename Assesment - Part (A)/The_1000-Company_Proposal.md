# The "Federer" Autonomous Sourcing Engine: A 30-Day Scale-Up Proposal



**Objective:** Build a highly qualified pipeline of 1,000 "Federer" MSMEs (₹50-500Cr, technical, promoter-led, specialty manufacturers) in 30 days.



**The Core Philosophy:** Manual research (Part A) is for algorithm design. Scaling (Part B) requires shifting from "Researcher" to "System Architect." To achieve this, we will build a 4-stage automated funnel using Clay.com as our central orchestrator, plugging into scraping APIs and LLMs to perform the 6-Criteria evaluation autonomously.



###### **Stage 1: The Top-of-Funnel Aggregator (Week 1)**

**Goal:** Cast a wide but mathematically precise net to gather 10,000 raw domains.

**Tools Used:** Apollo.io API, Phantombuster, Govt Database Scrapers.



* **The Action:** We cannot search "Specialty Manufacturers." Instead, we scrape proxy indicators of technical depth.



1. **Boolean Scraping (Apollo.io):** Filter for companies in India with 50–250 employees in target NIC codes (Chemicals, Biotech, Machinery).
2. **Regulatory Scraping:** Write a Python script to extract domain names of all companies listed in the DSIR R\&D Directory, the USFDA India Inspection List, and PLI Beneficiary PDFs.
3. **Expo Scraping:** Scrape exhibitor lists from the last 3 years of CPHI India, Analytica Anacon, and BioAsia.



* **The Output:** A raw list of \~10,000 company names, URLs, and LinkedIn URLs dumped into our central Clay table.



* **Yield Rate:** 10,000 Raw Leads.



###### Stage 2: The Semantic Classifier (Week 2)

**Goal:** Automate Criterion 1 (Manufacturer), 3 (Differentiated), and 4 (Tech DM) to eliminate commodities, traders, and software companies.

**Tools Used:** Clay (Web Scraper Integration) + Anthropic Claude 3.5 Sonnet API (for superior logical reasoning).



* **The Action:** We deploy AI to read websites exactly like a DeepThought analyst would.



* **The Execution Flow:**



**Step A (The Site Scrape):** Clay visits all 10,000 URLs and scrapes the Home, About Us, and Products text.



**Step B (The AI Interrogation):** We feed the text to Claude via API with this highly specific prompt:



"You are an M\&A analyst looking for 'Federer' MSMEs. Read this company data. Return a JSON payload. 1. Is this a physical product manufacturer, a trader, or a service/CRO? (Reject traders/services). 2. Are their products 'commodity' or 'specialty/niche'? 3. Is there evidence of patents, in-house R\&D, or complex formulations?"



**Step C (The Leadership Scrape):** Trigger a LinkedIn API call to scrape the Founder/MD's profile. Ask Claude: "Does this founder have a STEM degree (PhD/B.Tech) or purely commerce/finance?"



**Yield Rate:** \~60% disqualification (eliminating traders, generic pharma, and service labs). We enter Week 3 with 4,000 High-Potential Leads.



###### **Stage 3:** The Reality Check — Financial \& Ownership Triangulation (Week 3)

**Goal:** Automate Criterion 6 (Growth) and ensure they fit the strict MSME revenue/ownership constraints.

**Tools Used:** Tofler API / Zauba Corp API / LinkedIn Premium API.



* **The Action:** We must eliminate the "fakers" (companies that look great but are actually stagnant or PE-owned).



**The Execution Flow:**



1. **The Revenue \& Structure Ping (Tofler API):** Ping the remaining 4,000 companies.



Auto-Reject: Revenue < ₹40Cr or > ₹500Cr.



Auto-Reject: If parent company / holding company exists (eliminates Tata/Reliance subsidiaries and PE-owned entities like Suven Pharma).



2\. **The Growth Signal Ping (LinkedIn API):** Check the company's LinkedIn headcount growth over the last 12 months.



Pass condition: If headcount has grown by >5%, or if they have 5+ active job postings for technical roles (e.g., "Production Engineer", "QC Lead").



**Yield Rate:** \~60% disqualification (due to missing the tight revenue band or being corporate subsidiaries). We enter Week 4 with 1,600 "A-Band" Candidates.



###### Stage 4: Human-in-the-Loop \& Hyper-Personalization (Week 4)

**Goal:** Final quality control and generating the outreach assets to secure the 1,000 final list.

**Tools Used:** Human Analysts + OpenAI GPT-4o.



* **The Action:** AI hallucinates. Human judgment is required to finalize the pipeline.



* **Quality Control (Addressing False Positives):**



Sort the 1,600 leads by "AI Confidence Score."



Human analysts spot-check borderline cases. Specifically looking for "CROs disguised as Biotech manufacturers" (a common AI blindspot).



Discard the bottom 600 marginal fits.



* **The "Personalization Hook" Generator:**



For the final 1,000, we run a final prompt: "Analyze this company's latest news and tech. Write a one-sentence email opener complementing a specific recent technical achievement (e.g., an AS9100C certification or a new plant in Genome Valley)."



Humans review the hook, approve it, and finalize the CSV.



**Final Output: 1,000 perfectly profiled "Federer" companies.**



###### Anticipated Edge Cases \& Solutions

1. **"The Ghost MSME" (No Website):** Many brilliant technical founders have terrible, broken websites. Solution: If a company fails the Week 2 Website scrape but is present in the DSIR R\&D Govt list, bypass the AI website check and route directly to human review.



**2. The "Group Company" Illusion:** An MSME might report ₹100Cr, but it's secretly bankrolled by a ₹5,000Cr parent. Solution: Programmatic checks via Tofler for "Common Directors" with massive conglomerates.

