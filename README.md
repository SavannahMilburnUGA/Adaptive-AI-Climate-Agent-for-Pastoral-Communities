# Adaptive AI Climate Agent for Pastoral Communities
![A flock of sheep begins its descent into the valley at the end of summer, in the Soula Valley, on September 14, 2022 from https://www.theatlantic.com/photo/2022/09/new-generation-shepherds-french-pyrenees/671582/](https://cdn.theatlantic.com/thumbor/XQvLugXKNjHCvUNTdEyaok3jv2g=/1200x800/media/img/photo/2022/09/shepherdess/a06_1243417033/original.jpg)
**Expanding research I was lucky to be a part of on Dr. Tom Mote's WeatherRisk VIPR team @ The University of Georgia.**
## The Problem
Farming communities in the French Basque Pyrenees make critical decisions based on understanding seasonal climate patterns such as when to move livestock and how to manage pastures & optimize production. Climate scientists traditionally produce technical projections for farmers & stakeholders every year; however, these projections are not understandable or useful for the people who need them most. 
## The Solution
This prototype is a full-stack AI agent that models what a specific farmer believes about their future climate and adaptively selects & delivers physical climate storyline-inspired narratives co-produced between UGA's WeatherRisk VIPR team and French pastoralists in order to update that belief. Implementation was guided by Bayesian brain theory and the Free Energy Principle from computational neuroscience. 

Furthermore, instead of every farmer receiving the same climate information in the same order with the same framing, this AI climate agent tracks distinct belief states & chooses the proper climate narrative for the right farmer at the right moment in order to properly model real belief change. 
## Example
A skeptical farmer, Jean-Pierre, is assigned a 65% probability that the climate will not change. Say that Jean-Pierre messages the AI agent: 
> I remember 2022 being a very dry and difficult summer for grazing. 
The AI agent will recognize 2022 as the correct temporal analog for the Mediterranean Shift climate future (derived from VIPR research), retrieve experiential-register content referencing that year, & deliver it to Jean-Pierre. 

Jean-Pierre's belief for the Mediterranean Shift climate future rises from 10% to 17%, connecting an abstract climate future to an experience that Jean-Pierre actually lived through. The AI agent remembers this exchange & the next session will build on this persistent memory. 

## How It Works
* **RAG knowledge base**: 20 climate content chunks in ChromaDB from VIPR, retrieved by semantic similarity + re-ranked by belief-weighted informativeness
* **Probabilistic belief model**: farmer belief vector updates after every exhcange using heuristic Bayesian updating
* **ReAct agent loop**: LangGraph implements retrieve, rank, reason, respond, update belief for every message
* **Cross-session memory**: Mem0 stores key facts about each farmer across separate conversations
* **Free Energy Principle**: climate content selected to maximally reduce farmer uncertainty given their current belief state

### Tech Stack
**Backend**: Python, FastAPI, LangGraph, LangChain, ChromaDB, Mem0, Groq API <br>
**Frontend**: React, Next.js, Axios
> [!WARNING]
> This prototype uses Groq's free API tier (100,000 tokens/day). If the agent stops responding, the daily limit may have been reached. Please try again later. 