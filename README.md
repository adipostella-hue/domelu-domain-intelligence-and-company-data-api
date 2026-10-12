# Domelu: Email Domain Retrieval & Intelligence API 🚀

[![RapidAPI](https://rapidapi.com/adipostella/api/domelu1)
[![License](https://shields.io)](LICENSE)
[![Python](https://shields.io)](https://python.org)

**Domelu** is an enterprise-grade API designed to instantly turn any website domain into rich corporate intelligence, structured metadata, and verified employee emails with a single API call.

Stop wasting engineering sprints building and maintaining fragile web scrapers. Domelu unifies DNS lookups, web scraping, and deep database enrichment into a single latency-optimized request.

---

## ✨ Key Intelligence Layers

*   **🏢 Corporate Intelligence:** Extracts legal naming, company sizing ranges, estimated exact headcounts, and verified headquarters locations.
*   **✉️ Employee Intelligence:** Discovers primary/secondary corporate email patterns, department breakdowns, and lists verified executive profiles.
*   **🔒 Real-time MX & SMTP Verification:** Validates email hosts via live handshake checking to filter out risky or catch-all catchers.
*   **🌐 Social Proof & Metadata:** Automatically pulls tech-stacks, social channel links (LinkedIn, Twitter), meta descriptions, and domain trust scores.

---

## ⚡ Quick Start (Python)

### 1. Prerequisites
Ensure you have the `requests` package installed:
```bash
pip install requests
```

### 2. Integration Snippet
Create a file named `enrich_domain.py` and drop this clean boilerplate inside to pull full intelligence payloads:

```python
import requests

# 1. API endpoint details
url = "https://rapidapi.com"

# 2. Add your query parameters 
querystring = {
    "domain": "stripe.com",
    "include_layers": "dns_whois,web_scraping,enriched_db",
    "verify_emails": "true"
}

# 3. Securely pass your RapidAPI credentials
headers = {
    "X-RapidAPI-Key": "YOUR_RAPIDAPI_KEY_HERE",
    "X-RapidAPI-Host": "://rapidapi.com"
}

try:
    print(f"📡 Querying Domelu for: {querystring['domain']}...")
    response = requests.get(url, headers=headers, params=querystring)
    
    if response.status_code == 200:
        data = response.json()
        company = data['data']['company_profile']
        schema = data['data']['employee_intelligence']['employee_schema']
        
        print("\n✅ Success! Summary Received:")
        print(f"📍 Legal Name: {company['legal_name']}")
        print(f"📈 Estimated Headcount: {company['company_size']['estimated_exact']} employees")
        print(f"📬 Primary Email Pattern: {schema['primary_email_pattern']}")
    else:
        print(f"❌ Request failed with status code {response.status_code}")
        print(response.json())
        
except Exception as e:
    print(f"⚠️ An error occurred: {str(e)}")
```

---

## 📊 Sample Payload Output

A successful query returns a beautifully structured `200 OK` JSON response segmented by functional domains:

```json
{
  "status": "success",
  "code": 200,
  "request_id": "req_8f92a10c-4b7e-432d-91a5-e6f7a8b9c0d1",
  "timestamp": "2026-02-18T12:34:56.789Z",
  "execution_time_ms": 342,
  "data": {
    "company_profile": {
      "domain": "stripe.com",
      "company_name": "Stripe, Inc.",
      "legal_name": "Stripe, Inc.",
      "founding_year": 2010,
      "industry": "Financial Services & Fintech",
      "company_size": {
        "range": "5,000 - 10,000",
        "estimated_exact": 8000,
        "category": "Enterprise"
      },
      "hq": {
        "city": "South San Francisco",
        "state_province": "CA",
        "country": "United States"
      }
    },
    "employee_intelligence": {
      "employee_schema": {
        "total_headcount": 8000,
        "primary_email_pattern": "{first_initial}{last}@stripe.com",
        "secondary_email_pattern": "{first}.{last}@stripe.com"
      },
      "verified_emails": [
        {
          "email": "pcollison@stripe.com",
          "first_name": "Patrick",
          "last_name": "Collison",
          "title": "CEO & Co-Founder",
          "verification_status": "VERIFIED",
          "confidence_score": 99
        }
      ]
    }
  }
}
```

---

## 🛠️ API Endpoints Summary

If you don't require the full combined weight of the enrichment pipeline, Domelu allows you to query specialized, singular sub-endpoints to optimize bandwidth and speed:

| Endpoint | Method | Purpose |
| :--- | :--- | :--- |
| `/v1/domain/enrich` | `GET` | **Full Domain Intelligence Engine** (Runs all layers) |
| `/v1/domain/dns-whois` | `GET` | DNS registration, registrar ages, MX servers, SPF/DMARC flags |
| `/v1/domain/scrape` | `GET` | Extracts site meta descriptions, titles, and social tags |
| `/v1/domain/employees`| `GET` | Specific headcount tiers, email formulas, and executive arrays |

---

## 🚀 Getting Your API Key

1. Navigate to the **[RapidAPI Hub Gateway](https://domelu.io)**.
2. Sign up or log into your developer dashboard.
3. Subscribe to the **Domelu** service to generate your unique token layer `X-RapidAPI-Key`.
4. Replace `YOUR_RAPIDAPI_KEY_HERE` in your code snippet and you're ready to scale!

## 📄 License
This repository and code samples are open source and available under the [MIT License](LICENSE).
