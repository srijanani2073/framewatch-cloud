# FrameWatch  
**Asymmetric News Framing Detector with Cross-Lingual Drift Analysis**

FrameWatch is a cloud-native system that detects **bias in how news is written**, focusing on how different entities in the same statement are framed emotionally or linguistically. It goes beyond traditional sentiment analysis by comparing *who is portrayed more favorably* and how that changes across languages.

**Live Demo:**  
https://thankful-glacier-00f6d3500.2.azurestaticapps.net/

## Overview

Traditional sentiment analysis assigns a single polarity to a document. FrameWatch instead performs:

- **Entity-level analysis** (who is favored vs disfavored)
- **Framing comparison within the same sentence**
- **Cross-lingual drift detection** (how translation changes bias)

It introduces two core metrics:

- **FAS (Framing Asymmetry Score)**  
  Measures how differently two entities are framed in the same statement.

- **CFDS (Cross-Lingual Framing Drift Score)**  
  Measures how framing changes after translation.

## Key Features

- Detects **linguistic framing bias** (e.g., “killed” vs “died”)
- Performs **Named Entity Recognition (NER)** and **opinion mining**
- Supports **multi-language input**
- Identifies **translation-induced bias**
- Provides **entity-level sentiment comparison**
- Stores and indexes past analyses for search

## Architecture

FrameWatch is built using a multi-service **Microsoft Azure** pipeline:

- **Frontend:** Azure App Service (HTML/CSS/JS)
- **Storage:** Azure Blob Storage (raw + translated inputs)
- **Database:** Azure Cosmos DB (structured results)
- **AI Services:**
  - Azure AI Language (NER + Opinion Mining)
  - Azure Translator (language detection + translation)
- **Compute:** Azure Functions (scoring + pipeline logic)
- **Orchestration:** Azure Logic Apps (event-driven workflow)
- **Search:** Azure Cognitive Search (query past analyses)

### Pipeline Flow

1. User submits text  
2. Text stored in Blob Storage  
3. Logic App triggers processing pipeline  
4. Translation + entity extraction + scoring  
5. FAS and CFDS computed  
6. Results stored and displayed on dashboard  

## Core Metrics

**Framing Asymmetry Score (FAS)**  
- Range: `-1.0 to +1.0`  
- Positive → Entity A is favored  
- Negative → Entity B is favored  

**Cross-Lingual Framing Drift Score (CFDS)**  
- Range: `0.0 to 1.0`  
- Higher value → translation significantly alters bias  

## Example

> “20 killed in Country B, 15 dead in Country C”

Even though the facts are similar:
- “killed” implies agency and blame  
- “dead” is neutral  

FrameWatch detects this asymmetry and quantifies it.

## Use Cases

- Media bias analysis  
- Political speech comparison  
- Conflict reporting evaluation  
- Journalism education  
- NGO and policy research  

## Tech Stack

- Frontend: HTML, CSS, JavaScript  
- Backend: Python (Azure Functions)  
- Database: Cosmos DB (NoSQL)  
- Storage: Azure Blob Storage  
- AI: Azure AI Language + Translator  
- Search: Azure Cognitive Search  

## Status

- UI and dashboard implemented  
- Azure pipeline functional  
- Entity-level scoring working  
- Cross-lingual analysis integrated  
