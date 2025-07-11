# Roman Republic Rolodex - Technical Specification

## Project Overview

A conversational interface for querying the Digital Prosopography of the Roman Republic (DPRR) and related ancient world datasets. Built with NextJS, this tool enables graduate students and professional historians to perform complex prosopographical research using natural language queries that are converted to SPARQL.

## Target Users

- Graduate students conducting advanced research
- Professional historians and classicists
- Researchers working with Roman Republican prosopographical data

## Core Features

### Query Capabilities
The tool must support all types of prosopographical queries:
- **Biographical queries**: "Tell me about all senators from Latium who served during the Second Punic War"
- **Relationship mapping**: "Show me the family connections between the Cornelii and Julii"
- **Career trajectory analysis**: "Find all quaestors who later became consuls within 10 years"
- **Geographic/temporal patterns**: "Which magistrates had careers spanning both Rome and the provinces"
- **Multi-hop relationship queries**: "Find all consuls whose fathers were also consuls"
- **Complex temporal reasoning**: "Show senators active during both the Catiline conspiracy and Caesar's consulship"
- **Aggregation and statistical queries**: "How many praetors from each decade of the 1st century BCE?"
- **Comparative analysis**: "Compare the career patterns of novi homines versus patricians"

### Conversational Interface
- Handle ambiguous queries by asking clarifying questions
- Support follow-up queries that build on previous results
- Allow iterative query refinement ("Now exclude those who died in exile")
- Maintain conversation context and history

### Technical Transparency
- **Default interface**: Minimal and clean
- **Advanced visibility**: Show generated SPARQL queries
- **Query editing**: Allow users to modify generated SPARQL before execution
- **Export capabilities**: Save, share, and export queries for reuse
- **Raw data access**: Display RDF data alongside human-readable results

## Technical Architecture

### Frontend
- **Framework**: NextJS with client-side rendering
- **UI Components**: shadcn/ui
- **Styling**: Light theme (dark mode reserved for future enhancement)
- **State Management**: Client-side state management for conversation history

### Backend Integration
- **LLM Integration**: Vercel AI SDK supporting multiple models
- **Configuration**: API keys via .env files
- **Model Support**: Multiple LLM providers (OpenAI, Anthropic, local models)
- **No model switching**: Single model per conversation session

### Data Sources
Architecture must support:
- **Primary**: Digital Prosopography of the Roman Republic (DPRR) SPARQL endpoint
- **Secondary**: Related datasets (Pleiades, Trismegistos, other linked ancient world data)
- **Custom endpoints**: User-configurable SPARQL endpoints
- **Local data**: RDF data file imports for local analysis

### Schema Discovery
- **Hybrid approach**: Automatic introspection with manual override capability
- **Auto-discovery**: Introspect SPARQL endpoints for classes, properties, relationships
- **Manual configuration**: Support VoID descriptions and configuration files
- **Caching**: Cache and version discovered schemas
- **OWL support**: Load OWL ontology files directly

### Database
- **Solution**: libsql for local data storage
- **Purpose**: Query history, cached schemas, configuration

## Result Presentation

### Output Formats
- **Tabular data**: Presented as tables
- **Narrative results**: Natural language with markdown formatting
- **Simple relationships**: Mermaid.js graphs for very simple results only
- **Links**: Relevant links embedded in results

### Export Options
- CSV, JSON formats
- Academic citation formats
- Structured data for publications

## Error Handling & Performance

### Query Validation
- Validate generated SPARQL against endpoint schema before execution
- Provide helpful error messages for failures (timeout, syntax, endpoint unavailable)
- Suggest query refinements for empty or overwhelming results
- Attempt automatic fixes for invalid SPARQL
- Log failed queries for debugging and improvement

### Performance Management
- Implement timeouts and result limits
- Handle large result sets gracefully
- Warn users about potentially expensive queries
- Performance metrics tracking

## Metadata & Provenance

### Tracking Information
- Query execution timestamps and performance metrics
- SPARQL endpoint sources for each result
- Data source attribution and last-updated information
- Query generation details (LLM model, prompt version)
- Result confidence levels and uncertainty indicators
- Links to original source records

### Academic Features
- Generate citable permalinks for queries and results
- Export query sessions as structured data
- Provide recommended citation formats
- Support research reproducibility requirements

## Authentication & Access

### User Management
- **No authentication required**: Anonymous usage
- **Session-based**: Query history maintained per session
- **Deployment model**: Each user has their own hosted instance

## Deployment Architecture

### Containerization
- **Docker support**: Containerized for easy deployment
- **Deployment targets**: Vercel, self-hosted servers, university infrastructure
- **Resource configuration**: Configurable memory, CPU, storage limits

### Setup & Administration
- **Documentation**: Setup documentation for technical administrators
- **Backup support**: Query history and configuration backup/migration
- **Monitoring**: Logging and monitoring capabilities
- **Environment management**: Development/staging/production configurations

### Development Workflow
- **Testing**: Automated testing for frontend and SPARQL query generation
- **Database management**: Migration and schema management tools

## Implementation Inspiration

Based on the SPARQL-LLM project (https://github.com/sib-swiss/sparql-llm), incorporating:
- Retrieval-Augmented Generation (RAG) for query accuracy
- SPARQL query validation
- Metadata extraction compatible with knowledge graphs
- Vocabulary of Interlinked Datasets (VoID) support

## Success Criteria

1. **Accuracy**: Generate correct SPARQL queries for complex prosopographical research questions
2. **Usability**: Intuitive natural language interface requiring minimal technical knowledge
3. **Transparency**: Full visibility into query generation and data sources
4. **Performance**: Reasonable response times for complex queries
5. **Reproducibility**: Complete audit trail for academic citation and methodology documentation
6. **Flexibility**: Support for multiple data sources and custom configurations
7. **Reliability**: Robust error handling and recovery mechanisms

## Future Enhancements (Not in Scope)

- Dark mode theme
- User authentication system
- Collaborative features
- Advanced visualization beyond simple Mermaid graphs
- Real-time collaboration between researchers
- Integration with citation management tools