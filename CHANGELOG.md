# Changelog

## [2.4.0] - 2025-07-23

### Added
- **Security, Data Quality & Schema Registry Guide**: Comprehensive enterprise-grade guide covering multi-layered authentication, data encryption, access control implementation, and schema registry management
- **Messaging Strategies Guide**: Detailed implementation strategies organized by message type (command, event, request/response, document) and application domain (financial services, IoT, microservices)
- **Enhanced Best Practices**: Added sections on replay mechanisms and dead-letter queues with practical implementation guidance
- **Enterprise Security Patterns**: OAuth 2.0/JWT authentication, TLS 1.3 encryption, RBAC/ABAC access control with real-world configuration examples
- **Data Quality Framework**: Schema-driven quality assurance with validation pipelines, quality metrics, and alerting systems
- **Compliance Frameworks**: GDPR and HIPAA compliance configurations with data classification and retention policies
- **Practical Code Examples**: Over 1000 lines of configuration examples, Python implementations, and YAML templates
- **Mermaid Diagrams**: Visual architecture representations for authentication layers, validation pipelines, and message flow patterns

### Changed
- Updated mkdocs.yml navigation to include new implementation guides
- Enhanced Implementation section organization with logical guide ordering
- Updated version information to 2.4.0 across all documentation

### Technical
- Added messaging-strategies.md (400+ lines) with comprehensive message type implementations
- Added security-data-quality-guide.md (600+ lines) with enterprise security and quality patterns
- Enhanced best-practices.md with replay and DLQ sections
- Updated MkDocs configuration for new guide integration
- Maintained compatibility with existing Material theme and Mermaid support

## [2.3.3] - 2025-07-15

### Changed
- Updated materials.md documentation with missing .drawio files
- Enhanced reference section with complete diagram file listings
- Improved documentation completeness and consistency

### Technical
- Minor version bump for documentation updates
- Updated version information in mkdocs.yml and index.md

## [2.3.1] - 2025-07-15

### Changed
- Updated DrawIO diagram files across all messaging systems
- Added new diagram files for materials and selection criteria
- Maintained visual consistency across documentation
- Enhanced documentation assets for better visual representation

### Technical
- Minor version bump for diagram updates
- Updated version information in mkdocs.yml and index.md

## [2.3.0] - 2025-07-15

### Added
- Interactive Mermaid decision tree replacing text-based business decision tree
- RabbitMQ strategic positioning in business decision tree (3 key positions)
- Enhanced IoT integration with early filtering in requirements definition
- Bank Assurance use case added to Quick Reference Guide
- Decision node visualization with color-coded node types
- Strategic business drivers enhancement for cost, growth, advantage, risk, and innovation

### Changed
- Business decision tree now uses interactive Mermaid flowchart
- Quick Reference Guide includes Bank Assurance with IBM MQ + ActiveMQ recommendation
- Decision framework has better IoT requirements integration
- Enhanced visual design with color-coded decision nodes, solutions, and benefits

### Technical
- Mermaid flowchart implementation with decision nodes (diamond shapes)
- Strategic business driver routing with preference-based decisions
- Enhanced table formatting and content organization
- Updated version to 2.3.0 across all documentation

## [2.2.0] - 2025-07-15

### Added
- Comprehensive Apache ActiveMQ documentation with architecture diagrams
- Enhanced product comparison table with ActiveMQ capabilities
- Multi-protocol support analysis for messaging systems
- Enterprise integration patterns and JMS implementation guide
- Network of brokers architecture patterns for ActiveMQ
- Detailed configuration examples for single broker and HA setups

### Changed
- Updated MkDocs navigation to include ActiveMQ
- Enhanced 'What's New' section to reflect ActiveMQ addition
- Updated version information across all documentation

### Technical
- Added site/ directory to .gitignore (generated content)
- Removed generated site files from git tracking
- Updated mkdocs.yml with version 2.2.0
