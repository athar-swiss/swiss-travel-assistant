# Swiss Travel Assistant - M365 Copilot Declarative Agent

An AI agent that simplifies Swiss travel planning, demonstrating **practical AI governance** in action.

[![EU AI Act](https://img.shields.io/badge/EU%20AI%20Act-LOW%20RISK-green)](https://artificialintelligenceact.eu/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 🎯 Purpose

This declarative agent simplifies Swiss travel planning by providing:
- 🚂 Real-time SBB (Swiss Federal Railways) routes and schedules
- 🏔️ Swiss Tourism data (attractions, hotels, restaurants)
- 📅 Cantonal holiday calendars (important for planning)
- 💡 Personalized travel recommendations

Designed as a **governance reference** for organizations building M365 Copilot agents.

---

## 🏗️ Technical Architecture

### Platform
- **Microsoft 365 Copilot Studio** (Declarative Agent)
- **Natural language interface** (no coding required for users)
- **Read-only access** (no data modification)

### Data Sources
1. **SBB Open Data API**
   - Public transport routes, schedules, delays
   - Real-time departure/arrival information
   - License: [SBB Open Data Terms](https://opentransportdata.swiss)

2. **Switzerland Tourism Public API**
   - Attractions, hotels, restaurants
   - Events and activities
   - License: [MySwitzerland API Terms](https://www.myswitzerland.com)

3. **Cantonal Holiday Calendars**
   - Public holidays by canton
   - Source: Government open data (public domain)

### Integration Flow
```
User Query (natural language)
    ↓
M365 Copilot (intent detection)
    ↓
Swiss Travel Assistant (orchestration)
    ↓
├── SBB API (transport data)
├── Tourism API (attraction data)
└── Holiday Calendar (date validation)
    ↓
Consolidated Response (with citations)
```

---

## ⚖️ AI Governance Framework

### EU AI Act Classification: **LOW RISK** ✅

**Rationale:**
- ✅ **Read-only agent** (no autonomous actions or decisions)
- ✅ **Public data only** (no PII processing)
- ✅ **Advisory output** (user decides, agent suggests)
- ✅ **No high-risk domain** (not employment, law enforcement, critical infrastructure, border control)

**Result:** Minimal governance requirements (transparency encouraged, full audit not mandatory).

---

### Comprehensive Risk Assessment

| **Risk Factor** | **Level** | **Likelihood** | **Impact** | **Mitigation** |
|-----------------|-----------|----------------|------------|----------------|
| **Data Privacy** | **LOW** | Low | Low | No PII collected/processed |
| **Bias** | **LOW** | Low | Low | Public data, factual information only |
| **Security** | **LOW** | Low | Medium | Read-only access, no write permissions |
| **Hallucination** | **MEDIUM** | Medium | Medium | Sources cited, users verify recommendations |
| **Vendor Lock-In** | **LOW** | Low | Low | Declarative agent (portable logic) |

**Overall Risk Score (NIST AI RMF):**  
`Risk = (Low × Medium) + (Medium × Medium) = LOW-MEDIUM`

**Conclusion:** Acceptable risk for deployment with standard governance controls.

---

### Governance Checklist (Completed)

#### ✅ **Data Source Validation**
- [x] **SBB API**: Public, terms of service reviewed ✅
- [x] **Swiss Tourism**: Public, attribution provided ✅
- [x] **Holiday calendars**: Public domain (government data) ✅
- [x] **No personal data**: Confirmed (agent doesn't ask for DOB, passport, payment info) ✅

#### ✅ **Access Controls**
- [x] **Organization employees only** (M365 authentication enforced)
- [x] **No external sharing** (internal tool only)
- [x] **Usage logging enabled** (audit trail via Copilot Studio)

#### ✅ **Compliance (GDPR / Swiss FADP)**
- [x] **No personal data collection** ✅
- [x] **No profiling or behavioral tracking** ✅
- [x] **Transparent data sources** (agent cites SBB, Tourism, etc.) ✅
- [x] **Right to explanation** (user sees sources for recommendations) ✅

#### ✅ **Risk Mitigation**
- [x] **Hallucination risk**: Sources cited (user can verify)
- [x] **Security risk**: Read-only (cannot modify data)
- [x] **Bias risk**: Factual data (not subjective opinions)

#### ✅ **Documentation**
- [x] **Risk assessment**: Documented (this README)
- [x] **Data sources**: Documented with licenses
- [x] **Governance classification**: EU AI Act LOW RISK

---

## 📸 Example Interaction

**User:** "I need to travel from Lausanne to Zurich tomorrow morning. Any recommendations?"

**Swiss Travel Assistant:**
```
🚂 Here are your travel options from Lausanne to Zurich tomorrow:

Direct Trains (via SBB):
- 07:04 - 09:26 (2h 22m, IC 706)
- 08:04 - 10:26 (2h 22m, IC 708)
- 09:04 - 11:26 (2h 22m, IC 710)

💡 Recommendations:
- Book early for seat reservation (popular route)
- Zurich has no cantonal holidays tomorrow (offices open)
- Weather: Clear, 15°C (check current forecast)

🏔️ If you have time in Zurich:
- Visit Old Town (Altstadt) - 20 min walk from HB
- Lake Zurich promenade - scenic views
- Bahnhofstrasse shopping - near station

Sources: SBB Open Data, Switzerland Tourism
```

---

## 🎓 Lessons Learned (Governance Insights)

### 1. **Governance-First Design**
**Before writing any code**, classify the risk (EU AI Act: LOW RISK).

**Result:** Clear governance requirements from Day 1. No surprises during deployment.

### 2. **API Licensing Matters**
**Critical step:** Verify Terms of Service for ALL external data sources.

**Why?** Even public APIs may have:
- Attribution requirements
- Commercial use restrictions
- Rate limits that affect availability

**Action:** Document all API licenses in governance checklist.

### 3. **Documentation = Governance Control**
**Comprehensive documentation** (this README) serves as:
- ✅ Audit trail (proves due diligence)
- ✅ Risk communication tool (stakeholders understand risks)
- ✅ Compliance evidence (GDPR requires data source transparency)

### 4. **Low Risk ≠ No Governance**
**Even "simple" agents need assessment.**

**Mistake to avoid:**  
"It's just a travel bot, no governance needed" ❌

**Correct approach:**  
"Low risk, but still document classification, data sources, and controls" ✅

### 5. **Declarative Agents = Lower Lock-In Risk**
**Declarative agents** (vs. custom code) are more portable:
- Logic is configuration-based (not proprietary code)
- Can be recreated in other platforms if needed
- Lower vendor lock-in risk

**Example:** If leaving Copilot Studio, this agent's logic could be rebuilt in another agent framework in ~2 weeks.

---

## 🚀 How to Use This as a Reference

### For Your Own Agent Governance

1. **Copy the Risk Assessment Table**
   - Evaluate: Privacy, Bias, Security, Hallucination, Lock-In
   - Assign: Level + Likelihood + Impact + Mitigation

2. **Copy the Governance Checklist**
   - Adapt to your use case
   - Document: Data sources, access controls, compliance, documentation

3. **Classify by EU AI Act**
   - Use decision tree: Is it HIGH RISK? (employment, law enforcement, etc.)
   - If NO → LOW RISK (like this agent)
   - Apply appropriate governance level

4. **Document Everything**
   - Create README like this one
   - Makes your governance **auditable** and **transparent**

---

## 👤 About the Author

**Athar Sheikh**  
M365 + AI Governance Specialist  
18 years Microsoft 365 expertise

This agent demonstrates **practical application of AI governance frameworks** (NIST AI RMF, EU AI Act) to real-world M365 Copilot deployment.

**Certifications:**
- Azure AI Engineer Associate
- AI Fluency: Framework & Foundations
- Agent Explorer (Founderz Business School)

---

## 📄 License

MIT License

Copyright (c) 2025 Athar Sheikh

Permission is hereby granted, free of charge, to any person obtaining a copy of this documentation and associated materials, to deal in them without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies, and to permit persons to whom they are furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the materials.

---

## 🤝 Contributing

This is a **reference implementation** for governance best practices.

**Found this useful?**
- ⭐ **Star the repository** (helps others discover it)
- 🔗 **Link to this repo** in your own agent documentation

**Have questions?**  
Open an issue.

---

## 🏷️ Tags

`copilot-studio` `declarative-agent` `ai-governance` `eu-ai-act` `m365-copilot` `switzerland` `travel-assistant` `low-risk-ai` `nist-framework` `microsoft-365`

---

**Part of an AI Governance learning journey.**  
**Building practical frameworks, not just theory.** 🚀
