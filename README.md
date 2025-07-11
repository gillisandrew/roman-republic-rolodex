# Roman Republic Rolodex

ABOUTME: A conversational interface for querying the Digital Prosopography of the Roman Republic and related ancient world datasets.
ABOUTME: Built with Next.js, this tool enables graduate students and professional historians to perform complex prosopographical research using natural language queries.

## Overview

The Roman Republic Rolodex is a sophisticated chat-based interface that converts natural language queries into SPARQL queries, allowing researchers to interact with complex ancient world datasets without needing to know SPARQL syntax.

## Features

- **Natural Language Queries**: Ask questions in plain English about Roman Republican prosopography
- **SPARQL Generation**: Automatically generates and executes SPARQL queries
- **Multiple Data Sources**: Supports DPRR and other ancient world datasets
- **Transparent Results**: View generated queries, raw data, and formatted results
- **Export Capabilities**: Export results in various formats including CSV, JSON, and academic citations

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone https://github.com/gillisandrew/roman-republic-rolodex.git
cd roman-republic-rolodex
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.local.example .env.local
# Edit .env.local with your API keys and configuration
```

4. Start the development server:
```bash
npm run dev
```

5. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Development

### Scripts

- `npm run dev` - Start development server with Turbopack
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint
- `npm run type-check` - Run TypeScript type checking

### Project Structure

```
src/
├── app/                 # Next.js app router pages
├── components/          # Reusable UI components
├── lib/                 # Utility functions and configurations
├── types/              # TypeScript type definitions
└── hooks/              # Custom React hooks
```

## Contributing

This project follows a structured 18-step implementation plan. See `plan.md` for detailed development steps and `todo.md` for current progress.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Digital Prosopography of the Roman Republic (DPRR) - https://romanrepublic.ac.uk/
- Inspired by the SPARQL-LLM project - https://github.com/sib-swiss/sparql-llm
