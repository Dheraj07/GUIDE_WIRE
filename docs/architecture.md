# 🧠 System Architecture — RainGuard AI

## 📦 Components

### 👤 User Module
- User registration  
- Policy selection based on risk  

---

### 🌦️ Weather Data Module
- Fetches real-time environmental data  
- Integrates with external APIs (e.g., OpenWeather API)  

---

### 🤖 AI Risk Engine
- Uses historical + real-time data  
- Calculates disruption probability  
- Generates risk score (0–1)  
- Dynamically adjusts premium  

---

### ⚡ Trigger Engine
- Monitors parametric thresholds:
  - Rainfall > 10 mm  
  - Temperature > 42°C  
  - AQI > 300  
- Activates payout condition automatically  

---

### 🧾 Claims Engine
- No manual claim process  
- Auto-validates trigger events  
- Initiates claim instantly  

---

### 💳 Payment Module
- Processes payouts (simulated / Razorpay test mode)  
- Ensures quick fund transfer  

---

## 🔄 Data Flow

User → Location  
↓  
Weather API → AI Risk Engine  
↓  
Trigger Engine  
↓  
Claims Engine  
↓  
Payment System  

---

## 📊 Architecture Diagram

```mermaid
flowchart TD
    A[User] --> B[User Module]
    B --> C[Location Data]

    C --> D[Weather Data Module]
    D --> E[Weather API]

    E --> F[AI Risk Engine]
    F --> G[Risk Score Calculation]

    G --> H[Trigger Engine]

    H -->|Threshold Met| I[Claims Engine]
    H -->|No Trigger| J[Monitoring Continues]

    I --> K[Payment Module]
    K --> L[Payout to User]

    style A fill:#f9f,stroke:#333
    style F fill:#bbf,stroke:#333
    style H fill:#ffcc00,stroke:#333
    style I fill:#90ee90,stroke:#333
