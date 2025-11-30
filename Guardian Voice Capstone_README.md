# **Guardian Voice: AI-Powered Personal Safety Sentinel**

## **1\. The Pitch (Problem, Solution, Value)**

### **The Problem**

In critical safety situations, every second counts. Traditional safety apps often require manual interaction (unlocking a phone, finding an app, pressing a button), which is impossible during an active assault or panic situation. Furthermore, generic SOS alerts lack context—police receiving a "Help" ping don't know if it's a medical emergency, a kidnapping, or harassment, nor do they know the victim's identity or medical history immediately.

### **The Solution**

**Guardian Voice** is a hands-free, voice-activated safety agent. It uses a multi-agent AI system to:

1. **Listen** for a discreet, pre-recorded "Safe Word" in the background.  
2. **Analyze** the situation using context (location, user profile, battery health).  
3. **Orchestrate** a response: instantly alerting verified contacts and local authorities with a rich, AI-generated report that includes the user's photo, medical info, and live location.  
4. **Community Defense:** It enables a "Safe Ride" verification system and a crowdsourced safety map.

### **The Value**

* **Speed:** Zero-touch activation reduces response time significantly.  
* **Context:** AI-generated reports provide first responders with "who," "where," and "what" before they arrive.  
* **Trust:** The verified driver and community reporting features prevent danger before it happens.

## **2\. Technical Implementation (The "How")**

### **Key Concepts Applied (from Agents Intensive Course)**

We have implemented a **Multi-Agent System** powered by **Gemini 1.5 Flash** to handle complex decision-making.

1. **Multi-Agent System (Sequential & Parallel):**  
   * **Triage Agent:** Analyzes the voice transcript to classify the intent (Emergency, Ride Booking, or Incident Report).  
   * **Emergency Response Agent:** If danger is detected, this agent gathers context and drafts a precise SOS message.  
   * **Resource Agent:** Concurrently searches for the nearest police station/hospital (simulated tool use).  
2. **Tools (Function Calling):**  
   * The agents are equipped with custom tools: get\_user\_profile(), get\_gps\_location(), and search\_nearby\_services(). This allows the LLM to ground its response in real data rather than hallucinating.  
3. **Context Engineering:**  
   * The system injects a "System Prompt" containing the user's saved profile (Blood Group, Photo URL, Govt ID) into the context window. This ensures every alert is personalized and actionable.

### **Architecture**

* **Frontend:** HTML5/JS (Capture Voice & Location).  
* **Backend Agent:** Python (Gemini 1.5 Flash) handling the logic and decision routing.  
* **Database:** Firebase Firestore (Long-term memory for profiles/logs).

### **Effective Use of Gemini (Bonus)**

We utilize Gemini's speed and long context window to process voice transcripts in real-time and format complex JSON alerts for authorities.

## **3\. Setup & Usage**

1. **Prerequisites:** Python 3.9+, Google Cloud API Key (Gemini).  
2. **Install:** pip install google-generativeai  
3. **Run:** python safety\_agent.py  
4. **Simulation:** The script includes a main block that simulates a user saying their safe phrase to demonstrate the full agent workflow.