# 🔐 Full Stack (Backend-focused) Coding Challenge: Bittensor (TAO) Wallet API

## 📘 Overview

Design and implement a secure REST API for managing Bittensor (TAO) wallets. This challenge focuses on backend development, security best practices, and API design. Your solution should demonstrate production-ready code with proper authentication, encryption, and error handling.

---

## 🎯 Core Requirements

### 1. **POST /wallets** - Create New Wallet
- Generate a new Bittensor keypair (SS58 format)
- Securely encrypt and store the private key
- Return wallet ID and public address
- Implement proper password-based encryption
- **Security Focus**: Demonstrate secure key generation and storage

### 2. **GET /wallets/:id/balance** - Fetch Wallet Balance  
- Retrieve TAO balance from Bittensor network
- Handle network failures gracefully
- Implement caching strategies for performance
- **Challenge**: Work with Bittensor's substrate-based network

### 3. **POST /wallets/:id/transfer** - Transfer TAO
- Create and sign transactions
- Validate recipient addresses
- Implement transaction broadcasting
- Include proper fee calculation
- **Security Focus**: Transaction signing and validation

### 4. **🌟 Bonus: GET /wallets/:id/history** - Transaction History
- Return paginated transaction history
- Mock realistic transaction data
- Include transaction status tracking
- **Extra Credit**: Implement scheduled/recurring transactions

---

## 🛡️ Security Requirements

Your implementation **must** demonstrate:

- **Encryption at Rest**: Private keys must be encrypted using industry standards
- **Authentication**: API endpoints should be protected (JWT/API keys)
- **Input Validation**: Proper sanitization and validation of all inputs
- **Error Handling**: No sensitive information leaked in error responses
- **Rate Limiting**: Prevent abuse of wallet creation and transfer endpoints
- **Audit Logging**: Log security-relevant events

---

## 🏗️ Technical Requirements

### Backend Stack (Choose Your Preference)
- **Node.js** (Express/Fastify) + TypeScript
- **Python** (FastAPI/Django) 
- **Go** (Gin/Echo)
- **Rust** (Axum/Actix)

### Database
- Design appropriate schema for wallet storage
- Consider both SQL and NoSQL approaches
- Implement proper indexing strategies

### Bittensor Integration
- Use official Bittensor libraries where available
- Handle network connectivity issues
- Implement proper error codes for different failure scenarios

---

## 📋 Deliverables

### 1. **Production-Ready API**
- RESTful endpoint implementation
- Comprehensive error handling
- Input validation and sanitization
- Security middleware implementation

### 2. **Database Design**
- Schema design with proper relationships
- Migration scripts
- Consider data encryption requirements

### 3. **Documentation**
- OpenAPI/Swagger specification
- Setup and deployment instructions
- Security considerations document
- API usage examples

### 4. **Testing Suite**
- Unit tests for core functionality
- Integration tests for API endpoints
- Security-focused test cases
- Mock external dependencies

### 5. **Configuration**
- Environment-based configuration
- Docker containerization
- Basic monitoring/health checks

---

## 🧪 Evaluation Criteria

### Primary Focus Areas:
- **🔒 Security Implementation** (30%)
  - Key encryption and storage
  - Authentication and authorization
  - Input validation and sanitization
  - Secure error handling

- **🏗️ API Design & Architecture** (25%)
  - RESTful design principles
  - Error handling strategies  
  - Code organization and patterns
  - Database design decisions

- **🔧 Technical Implementation** (20%)
  - Code quality and readability
  - Performance considerations
  - Error handling and edge cases
  - Testing coverage

- **📚 Documentation & DevOps** (15%)
  - API documentation quality
  - Setup instructions clarity
  - Configuration management
  - Deployment considerations

- **🚀 Problem-Solving** (10%)
  - Handling Bittensor integration challenges
  - Creative solutions to limitations
  - Performance optimizations

---

## 🎁 Bonus Features (Extra Credit)

- **Advanced Security**: Hardware Security Module (HSM) integration concepts
- **Monitoring**: Comprehensive logging and metrics
- **Advanced Features**: Multi-signature wallet support
- **Scalability**: Caching layer and database optimization
- **DevOps**: CI/CD pipeline configuration
- **Scheduled Transactions**: Recurring payment system

---

## 📝 Submission Guidelines

### Required Files:
```
├── README.md              # Setup and API documentation
├── API_SPEC.md            # Detailed API specification  
├── SECURITY.md            # Security implementation details
├── src/                   # Source code
├── tests/                 # Test suite
├── docs/                  # Additional documentation
├── docker-compose.yml     # Local development setup
└── .env.example          # Environment configuration template
```

### README Must Include:
- **Quick Start Guide**: How to run locally in < 5 minutes
- **API Documentation**: All endpoints with examples
- **Security Approach**: Explanation of security measures
- **Database Schema**: Entity relationships and design decisions
- **Testing Instructions**: How to run the test suite
- **Deployment Notes**: Production deployment considerations

---

## 🔗 Useful Resources

- [Bittensor Documentation](https://docs.bittensor.com/)
- [SS58 Address Format](https://github.com/paritytech/substrate/wiki/External-Address-Format-(SS58))
- [Substrate RPC API](https://polkadot.js.org/docs/substrate/rpc)


## 🚀 Submission

Submit a **public GitHub repository** with:
1. Complete, runnable code
2. Comprehensive documentation
3. Test suite with good coverage
4. Docker setup for easy evaluation

**Good luck! We're excited to see your approach to building secure, scalable backend systems.**

---

*This challenge is designed to evaluate real-world backend development skills, security awareness, and API design capabilities. Focus on code quality, security, and documentation over feature completeness.* 

*Feel free to use all the tools that you wish that are at your disposal. Use AI tools if you find them necessary! But, just know that in the technical interview where we go over the submission, we might ask you to think deeply and replicate some aspects of the code without AI assistance.* 
