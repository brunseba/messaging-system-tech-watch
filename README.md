# Messaging System Tech Watch

A comprehensive technical documentation and evaluation guide for messaging systems including Apache Kafka, RabbitMQ, Apache Pulsar, NATS, Redis, and more.

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/brunseba/messaging-system-tech-watch.git
   cd messaging-system-tech-watch
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

### Development

1. **Serve the documentation locally**
   ```bash
   mkdocs serve
   ```
   The documentation will be available at `http://localhost:8000`

2. **Build the documentation**
   ```bash
   mkdocs build
   ```

3. **Deploy to GitHub Pages**
   ```bash
   mkdocs gh-deploy
   ```

## 📁 Project Structure

```
messaging-system-tech-watch/
├── docs/                                    # Documentation source
│   ├── index.md                            # Homepage
│   ├── requirements/                       # Requirements analysis
│   │   ├── functional-vs-non-functional.md
│   │   └── requirements-mapping.md
│   ├── decision-framework/                 # Decision framework
│   │   ├── decision-tree.md
│   │   └── selection-criteria.md
│   ├── solutions/                          # Messaging solutions
│   │   ├── architecture-overview.md
│   │   ├── product-comparison.md
│   │   └── developer-guide.md
│   ├── implementation/                     # Implementation guides
│   │   ├── deployment-guide.md
│   │   └── best-practices.md
│   └── use-cases/                          # Use case examples
│       ├── enterprise-integration.md
│       ├── iot-messaging.md
│       ├── microservices.md
│       └── real-time-analytics.md
├── inputs/                                 # Research and input files
├── mkdocs.yml                              # MkDocs configuration
├── requirements.txt                        # Python dependencies
└── README.md                              # This file
```

## 🛠️ Features

- **Interactive Decision Tree**: Mermaid diagrams for guided selection
- **Comprehensive Comparisons**: Detailed product and feature comparisons
- **Real-world Use Cases**: Practical examples and case studies
- **Dark/Light Mode**: Toggle between themes
- **Search Functionality**: Full-text search across all documentation
- **Mobile Responsive**: Works on all devices
- **Git Integration**: Last updated timestamps and contributor information

## 🔧 Configuration

The MkDocs configuration includes:

- **Material Theme**: Modern, responsive design
- **Mermaid Support**: Interactive diagrams and decision trees
- **Code Syntax Highlighting**: Syntax highlighting for code blocks
- **Search**: Advanced search capabilities
- **Git Integration**: Automatic timestamps and revision tracking
- **Minification**: Optimized for production deployment

## 📝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `mkdocs serve`
5. Submit a pull request

## 📚 Documentation Sections

### Requirements Analysis
- Understanding functional vs non-functional requirements
- Mapping requirements to technical capabilities

### Decision Framework
- Interactive decision tree for system selection
- Comprehensive selection criteria

### Messaging Solutions
- Architecture patterns overview
- Detailed product comparisons
- Developer-focused guides

### Implementation
- Step-by-step deployment guides
- Industry best practices

### Use Cases
- Enterprise integration patterns
- IoT messaging scenarios
- Microservices communication
- Real-time analytics implementations

## 🎯 Target Audience

- **Business Analysts**: Understanding requirements and making recommendations
- **Technical Architects**: Designing messaging system architectures
- **Developers**: Implementing messaging solutions
- **DevOps Engineers**: Deploying and maintaining messaging systems
- **Decision Makers**: Choosing the right messaging technology

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Support

For support and questions:
- Open an issue in the GitHub repository
- Check the documentation at [https://brunseba.github.io/messaging-system-tech-watch](https://brunseba.github.io/messaging-system-tech-watch)
- Contact the Business Technology Team

## 📋 Version

Current version: 2.1.0

### Recent Updates
- Added CloudEvents and AsyncAPI standards documentation
- Enhanced Kubernetes operator deployment guides with CRD details
- Expanded RabbitMQ Messaging Topology Operator coverage
- Added Mermaid.js diagrams for CRD relationships
- Improved message format standards documentation
