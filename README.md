# Civic Assistance Platform

> **Empowering citizens with voice-first access to government services**

A Progressive Web App that democratizes access to government services through conversational AI. Citizens ask questions in their language, the platform understands their needs, and connects them to relevant programs—all on a 2G connection.

![Platform Overview](./docs/images/platform-overview.png)

---

## 🎯 Problem Statement

Citizens struggle to discover and access government services due to:
- **Information barriers** - Complex bureaucratic language and scattered resources
- **Language constraints** - Limited support for local languages
- **Dependency on middlemen** - Corruption and exploitation through intermediaries

## ✨ Solution

A voice-first AI assistant that:
- Works on **2G networks** for underserved communities
- Speaks **local languages** natively
- Directly connects people to **healthcare, jobs, education, and legal resources**
- Operates **offline** with intelligent caching
- Prioritizes **accessibility** for all abilities

## 🚀 Key Features

### 1. Voice-First Interface
- Natural conversation in local languages
- Real-time speech-to-text transcription
- Text-to-speech responses with natural prosody
- Visual confirmation of understood queries

![Voice Interface](./docs/images/voice-interface.png)

### 2. Intelligent Service Discovery
- Eligibility matching based on demographics
- Semantic search across service descriptions
- Alternative suggestions when ineligible
- Regional filtering and inclusive program prioritization

![Service Discovery](./docs/images/service-discovery.png)

### 3. Low-Bandwidth Optimization
- Operates efficiently on 2G connections (< 100 kbps)
- Core functionality loads in 5 seconds
- Text-prioritized content delivery
- Intelligent caching for offline access

### 4. Accessibility First
- WCAG 2.1 Level AA compliant
- Screen reader support
- Keyboard navigation
- Adjustable text size and high-contrast modes
- Alternative text for all visual content

![Accessibility Features](./docs/images/accessibility.png)

### 5. Privacy & Security
- AES-256 encryption for stored data
- TLS 1.3+ for data in transit
- Consent-based data sharing
- Audit logging for compliance
- 30-day session retention policy

### 6. Feedback & Continuous Improvement
- Simple helpful/not helpful mechanism
- Issue flagging for common problems
- Incorrect information reporting
- Analytics-driven improvements

---

## 📋 Supported Services

The platform connects citizens to:

| Category | Examples |
|----------|----------|
| **Healthcare** | Government hospitals, health schemes, wellness programs |
| **Welfare** | Social security, subsidies, assistance programs |
| **Employment** | Job training, skill development, apprenticeships |
| **Education** | Scholarships, vocational training, educational institutions |
| **Legal** | Legal rights, aid services, grievance redressal |

---

## 🌍 Supported Languages

- English (en)
- Hindi (hi)
- Bengali (bn)
- Telugu (te)
- Marathi (mr)
- Tamil (ta)
- Gujarati (gu)

*More languages can be added based on demand*

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                  Progressive Web App                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Voice        │  │ Query        │  │ Offline      │  │
│  │ Interface    │  │ Processor    │  │ Cache Mgr    │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
           │                │                │
           ▼                ▼                ▼
┌─────────────────────────────────────────────────────────┐
│              Service Layer (Backend)                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ NLP Service  │  │ Service      │  │ Profile      │  │
│  │              │  │ Discovery    │  │ Manager      │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
           │                │                │
           ▼                ▼                ▼
┌─────────────────────────────────────────────────────────┐
│              Data Layer                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Services DB  │  │ User         │  │ Feedback     │  │
│  │              │  │ Profiles     │  │ Analytics    │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 📊 Requirements Overview

### Requirement 1: Healthcare and Welfare Service Discovery
- Identify matching healthcare services and welfare programs
- Display complete service information (eligibility, process, documents, contact)
- Suggest alternatives when ineligible

### Requirement 2: Job and Skill Program Access
- Return relevant job training and skill development programs
- Include program duration, certification, and enrollment details
- Provide regional apprenticeship information

### Requirement 3: Education Opportunity Discovery
- Identify scholarships and educational institutions
- Prioritize inclusive access programs
- Provide vocational training alternatives

### Requirement 4: Legal Rights Information Access
- Provide legal information in simple language
- Include law references and grievance mechanisms
- Break down complex information into steps

### Requirement 5: Local Language and Voice-First Interface
- Convert speech to text with sufficient accuracy
- Support text-to-speech in selected language
- Maintain language preference throughout session
- Provide visual confirmation of voice input

### Requirement 6: Low-Bandwidth Accessibility
- Operate in Low_Bandwidth_Mode below 100 kbps
- Prioritize text over multimedia
- Load core functionality in 5 seconds on 2G
- Provide text-only fallback on load failure

### Requirement 7: Inclusion and Accessibility Features
- WCAG 2.1 Level AA compliance
- Screen reader support
- Keyboard navigation
- Adjustable text size and contrast
- Alternative text for visual content
- Accessible forms with clear labels

### Requirement 8: Query Understanding and Response Generation
- Parse intent and extract key information
- Ask clarifying questions for ambiguous queries
- Use simple, jargon-free language
- Respond within 3 seconds for 90% of queries
- Maintain conversation context

### Requirement 9: Service Information Accuracy and Updates
- Display last update date for all services
- Update database within 24 hours of changes
- Cite official sources
- Indicate uncertainty when accuracy cannot be verified

### Requirement 10: Privacy and Data Security
- Encrypt data in transit (TLS 1.3+)
- Encrypt stored data (AES-256)
- Require explicit consent for data sharing
- Clear sensitive data on session end
- Allow data deletion on request
- Log all data access

### Requirement 11: User Feedback and Improvement
- Offer helpful/not helpful feedback mechanism
- Allow detailed feedback on "not helpful"
- Store feedback for analysis
- Flag items with common issues
- Provide incorrect information reporting

### Requirement 12: Session Management and Continuity
- Offer session resumption for returning users
- Maintain 30-day session history
- Save conversations on explicit session end
- Sync data across devices for logged-in users
- Allow query history viewing

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | TypeScript, PWA, Service Workers |
| **Voice** | Web Speech API, Deepgram/AssemblyAI |
| **NLP** | IndicBERT, mBERT, fast-check |
| **Storage** | IndexedDB, Cache API |
| **Encryption** | AES-256, TLS 1.3+ |
| **Testing** | Jest, fast-check (Property-Based Testing) |
| **Backend** | Node.js, REST API |
| **Database** | PostgreSQL |

---

## 📈 Performance Targets

| Metric | Target |
|--------|--------|
| Query Response Time | < 3 seconds (90th percentile) |
| Core Load Time (2G) | < 5 seconds |
| Voice Latency | < 500ms |
| Offline Availability | 100% for cached content |
| WCAG Compliance | Level AA |

---

## 🔐 Security & Privacy

- **Data Encryption**: AES-256 for storage, TLS 1.3+ for transit
- **Consent Management**: Explicit opt-in for data sharing
- **Audit Logging**: All data access logged for compliance
- **Session Cleanup**: Automatic sensitive data removal
- **Data Deletion**: User-initiated deletion on request

---

## 📦 Installation & Setup

### Prerequisites
- Node.js 16+
- npm or yarn
- Modern browser with Service Worker support

### Quick Start

```bash
# Clone repository
git clone https://github.com/yourusername/civic-assistance-platform.git
cd civic-assistance-platform

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Run tests
npm test

# Run property-based tests
npm run test:pbt
```

---

## 🧪 Testing Strategy

### Unit Tests
- Specific examples and edge cases
- Component integration points
- Error conditions

### Property-Based Tests
- Service matching accuracy across all profiles
- Language persistence across sessions
- Encryption for all data types
- Accessibility for all UI components

**Minimum 100 iterations per property test** using [fast-check](https://fast-check.dev/)

---

## 📚 Documentation

- [Requirements Document](./docs/REQUIREMENTS.md)
- [Design Document](./docs/DESIGN.md)
- [Implementation Plan](./docs/TASKS.md)
- [API Documentation](./docs/API.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

### Development Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📋 Project Status

- [x] Requirements finalized
- [x] Architecture designed
- [x] Implementation plan created
- [ ] Core infrastructure setup
- [ ] Data models implementation
- [ ] Service discovery component
- [ ] NLP service component
- [ ] Voice interface component
- [ ] Offline cache manager
- [ ] User profile manager
- [ ] UI integration
- [ ] Testing & QA
- [ ] Deployment

---

## 🎓 Learning Resources

- [Progressive Web Apps](https://web.dev/progressive-web-apps/)
- [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [IndexedDB Guide](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
- [Property-Based Testing](https://hypothesis.works/)

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/civic-assistance-platform/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/civic-assistance-platform/discussions)
- **Email**: support@civicassistance.org

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](./LICENSE) file for details.

---

## 🙏 Acknowledgments

- Government service data providers
- Accessibility advocates and testers
- Open-source community contributors
- Citizens who provided feedback

---

## 🌟 Impact

By democratizing access to government services, this platform aims to:
- **Reduce corruption** through direct service access
- **Improve digital inclusion** for underserved communities
- **Increase trust** in public systems
- **Empower citizens** with information and resources

---

**Made with ❤️ for digital inclusion**

