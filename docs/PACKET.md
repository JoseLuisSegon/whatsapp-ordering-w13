# BUSINESS BENDING PACKET: WhatsApp-Native B2B Ordering for Mexican Micro-Retailers

## 1. Problem Statement
Traditional hardware store and tiendita owners in Mexico (e.g., Col. Doctores, CDMX) suffer from severe morning stockouts and delivery delays, losing $800–$1,200 MXN weekly. They handle supplier restocking via unstructured, chaotic WhatsApp voice notes and phone calls. Forcing them to adopt standalone web dashboards or mobile apps causes 100% Day 1 churn due to tax distrust, device fatigue, and deeply ingrained WhatsApp habits.

## 2. Exact User Profile
A 42-year-old independent hardware store (ferretería) owner in Mexico City who manages inventory entirely through WhatsApp and refuses to use third-party desktop enterprise software ("aplicaciones raras").

## 3. Success Definition
By the module deadline, a fully functional prototype deployed on Vercel simulates an invisible WhatsApp-to-database ordering engine where merchants send unstructured voice/text notes, the system parses them into structured order summaries, and requires an explicit numeric confirmation ("Reply 1 to confirm") before dispatching to prevent costly errors.

## 4. Image-Generated Mockup Prompt (for v0 / AI generator)
"A mobile chat interface mockup of WhatsApp Business showing a chaotic voice note from a hardware store owner asking for cement and nails, followed immediately by an automated clean system text response: 'Order #402: 2 bags of cement, 1 box of nails. Reply 1 to confirm, 2 to edit.' Clean, minimalist, dark mode chat bubbles."

## 5. Process & Actor Flow (Mermaid Diagram)
```mermaid
sequenceDiagram
    autonumber
    actor Merchant as Micro-Retailer (WhatsApp)
    participant Bot as LLM WhatsApp API Backend
    participant System as Inventory & Dispatch System
    
    Merchant->>Bot: Sends chaotic voice note/text ("Oye mándame clavos...")
    Bot->>System: Parses audio/text & checks regional stock
    System-->>Bot: Generates structured summary
    Bot-->>Merchant: Sends summary + "Reply 1 to confirm"
    Merchant->>Bot: Replies "1" (Explicit Confirmation)
    Bot->>System: Locks order & sets delivery window
    6. Global Benchmark & Local Translation Line
Global Benchmark: Southeast Asian and Brazilian B2B micro-retail supply chain digitizers (e.g., BukuWarung / Meragro).
Local Translation: While global tools rely on native app downloads and fintech QR codes (like Pix), Mexican traditional hardware merchants reject standalone software due to SAT (tax) visibility fears and habituation to WhatsApp. Our tool localizes by operating 100% invisibly inside WhatsApp APIs without requiring app installations.
7. Long-View Charter (3 Years)
If this initial ordering slice succeeds, the product scales into an invisible supply-chain aggregator for over one million traditional micro-retailers across Mexico. It standardizes fragmented regional distribution networks through automated conversational commerce, transforming chaotic voice notes into predictable B2B logistics pipelines.
8. Scope Cuts (What we are NOT building)
No integrated real-time bank payment gateways (Stripe/CIE) for this sprint; payments remain handled via traditional credit/cash terms upon delivery.
No complex multi-user permission dashboards for accountants.
9. Architecture & Stack Table
Layer	Technology	Purpose
Frontend / UI	Next.js (via v0) + Tailwind CSS	Clean, responsive web simulation of the WhatsApp bot dashboard and order preview logs.
Backend / API	Next.js API Routes / Vercel Serverless	Handles order parsing logic and mock WhatsApp webhook routing.
Database & Auth	Supabase (PostgreSQL)	Stores order states, merchant profiles, and audit event logs. Secured with Row Level Security (RLS).
10. Test Plan
Mechanical Test: Inject ambiguous voice inputs (e.g., slang units like "un bulto" vs "una caja") to verify that the parsing engine catches ambiguity and successfully halts dispatch until explicit numeric confirmation ("1") is received.
Persona Test: Walk a synthetic median user (Doña Mari / Don Pancho) through the interface to log and resolve friction points.
