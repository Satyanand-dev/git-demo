# Project Manual
## An Explainable Machine Learning Framework for Railway Predictive Maintenance
### Using Data Streams from Metro Operator of Portugal

---

## 1. Project Overview

### 1.1 Problem Statement
Railway systems generate vast amounts of operational data. Effective predictive maintenance requires understanding **when** and **why** equipment might fail. This project aims to build an **explainable ML framework** that:
- Predicts maintenance needs from streaming data
- Provides interpretable explanations for predictions
- Supports decision-making for maintenance teams

### 1.2 Objectives
1. **Primary**: Develop an explainable ML model for predictive maintenance
2. **Secondary**: Process real-time data streams from metro systems
3. **Tertiary**: Generate actionable insights for maintenance scheduling

---

## 2. System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    DATA SOURCES                          │
├─────────────────────────────────────────────────────────┤
│  Metro Sensors  │  Maintenance Logs  │  Operational Data │
└────────┬────────┴────────┬───────────┴────────┬─────────┘
         │                 │                    │
         ▼                 ▼                    ▼
┌─────────────────────────────────────────────────────────┐
│                  DATA PIPELINE                          │
├─────────────────────────────────────────────────────────┤
│  Stream Processing  │  Data Cleaning  │  Feature Store   │
└────────┬────────────┴────────┬────────┴────────┬────────┘
         │                     │                 │
         ▼                     ▼                 ▼
┌─────────────────────────────────────────────────────────┐
│                 ML FRAMEWORK                            │
├─────────────────────────────────────────────────────────┤
│  Model Training  │  Explainability  │  Evaluation       │
└────────┬─────────┴────────┬────────┴────────┬──────────┘
         │                  │                 │
         ▼                  ▼                 ▼
┌─────────────────────────────────────────────────────────┐
│                  OUTPUT LAYER                            │
├─────────────────────────────────────────────────────────┤
│  Predictions  │  Explanations  │  Dashboard/API         │
└─────────────────────────────────────────────────────────┘
```

---

## 3. Data Requirements

### 3.1 Data Sources
| Source | Description | Format |
|--------|-------------|--------|
| Sensor Data | Vibration, temperature, pressure readings | Time-series |
| Maintenance Logs | Historical repair records | Structured/Unstructured |
| Operational Data | Train schedules, load factors | Tabular |
| Environmental Data | Weather, track conditions | Mixed |

### 3.2 Data Features
- **Temporal Features**: Timestamps, time since last maintenance
- **Operational Features**: Speed, load, usage hours
- **Sensor Features**: Multiple sensor readings per component
- **Target Variable**: Failure/no-failure within time window

---

## 4. Methodology

### 4.1 Data Preprocessing
```
Step 1: Data Collection → Step 2: Cleaning → Step 3: Feature Engineering
         ↓                     ↓                    ↓
   Handle missing values   Remove outliers    Create domain features
   Normalize scales        Align timestamps   Aggregate statistics
```

### 4.2 Model Selection
| Model Type | Purpose | Explainability |
|------------|---------|----------------|
| Random Forest | Baseline prediction | Medium (feature importance) |
| XGBoost/LightGBM | High-performance prediction | Medium (SHAP values) |
| LSTM/GRU | Sequential patterns | Low (requires interpretation) |
| TabNet | Attention-based | High (attention weights) |

### 4.3 Explainability Methods
1. **SHAP (SHapley Additive exPlanations)** - Feature contribution
2. **LIME (Local Interpretable Model-agnostic Explanations)** - Local predictions
3. **Attention Mechanisms** - Model-internal explanations
4. **Counterfactual Explanations** - "What-if" scenarios

---

## 5. Implementation Steps

### Phase 1: Setup (Week 1-2)
- [ ] Set up development environment
- [ ] Configure data pipeline
- [ ] Establish baseline metrics

### Phase 2: Data Pipeline (Week 3-4)
- [ ] Implement data ingestion
- [ ] Build preprocessing pipeline
- [ ] Create feature store

### Phase 3: Model Development (Week 5-8)
- [ ] Train baseline models
- [ ] Implement explainability modules
- [ ] Optimize model performance

### Phase 4: Integration (Week 9-10)
- [ ] Build prediction API
- [ ] Create explanation dashboard
- [ ] Integrate with maintenance systems

### Phase 5: Testing & Validation (Week 11-12)
- [ ] Validate with historical data
- [ ] Conduct user acceptance testing
- [ ] Performance benchmarking

---

## 6. Technology Stack

### 6.1 Core Technologies
```
Programming:    Python 3.9+
ML Framework:   scikit-learn, XGBoost, PyTorch
Stream Processing: Apache Kafka / Apache Flink
Database:       PostgreSQL + TimescaleDB
Visualization:  Plotly, Dash, Streamlit
```

### 6.2 Explainability Libraries
```
SHAP:           shap
LIME:           lime
InterpretML:    interpret
ELI5:           eli5
```

### 6.3 Deployment
```
Containerization: Docker
Orchestration:   Kubernetes (optional)
API:              FastAPI / Flask
Cloud:            AWS / GCP / Azure (if applicable)
```

---

## 7. Evaluation Metrics

### 7.1 Model Performance
| Metric | Target | Description |
|--------|--------|-------------|
| Accuracy | >85% | Overall correct predictions |
| Precision | >80% | Avoid false maintenance alerts |
| Recall | >90% | Catch actual failures |
| F1-Score | >85% | Balanced metric |
| AUC-ROC | >0.90 | Discrimination ability |

### 7.2 Explainability Metrics
| Metric | Target | Description |
|--------|--------|-------------|
| Faithfulness | >80% | Explanations match model behavior |
| Stability | >90% | Consistent explanations |
| Comprehensibility | Qualitative | Human-understandable |

---

## 8. Deliverables

### 8.1 Technical Deliverables
1. Trained ML models (with checkpoints)
2. Explainability pipeline code
3. Data processing pipeline
4. REST API for predictions
5. Dashboard for visualization

### 8.2 Documentation
1. Technical documentation
2. API documentation
3. User guide
4. Model cards (for each model)

---

## 9. Risk Management

| Risk | Impact | Mitigation |
|------|--------|------------|
| Data quality issues | High | Implement validation checks |
| Model overfitting | Medium | Cross-validation, regularization |
| Explainability trade-offs | Medium | Multiple explanation methods |
| Scalability issues | Low | Design for streaming from start |

---

## 10. Success Criteria

### 10.1 Minimum Viable Product (MVP)
- [ ] Model predicts failures with >80% recall
- [ ] Explanations are generated for each prediction
- [ ] API serves predictions in <100ms
- [ ] Dashboard displays predictions + explanations

### 10.2 Final Product
- [ ] All MVP criteria met
- [ ] Real-time streaming capability
- [ ] Integration with maintenance planning system
- [ ] User acceptance from maintenance team

---

*Document Version: 1.0*
*Last Updated: {Current Date}*
