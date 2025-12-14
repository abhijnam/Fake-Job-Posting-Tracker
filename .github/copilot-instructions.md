# Copilot Instructions for SafeHire

## Project Overview

SafeHire is an AI-powered fake job posting detection tool designed to help newcomers to Canada identify fraudulent job postings. The application analyzes job descriptions and provides a trust score with explanations of potential red flags.

## Repository Structure

This is a **monorepo** managed with **Yarn workspaces**:

```
Fake-Job-Posting-Tracker/
├── packages/
│   ├── frontend/     # React + TypeScript + Vite + Tailwind CSS
│   └── backend/      # Python + FastAPI + scikit-learn
└── shared/           # Shared utilities and types
```

## Tech Stack

### Frontend (`packages/frontend/`)
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite 6
- **Styling**: Tailwind CSS 4 + Radix UI components
- **Routing**: React Router DOM
- **UI Libraries**: Radix UI, Lucide React icons
- **Forms**: React Hook Form

### Backend (`packages/backend/`)
- **Framework**: FastAPI (Python)
- **Server**: Uvicorn
- **ML/AI**: scikit-learn for model training and inference
- **Data Processing**: pandas, numpy
- **OCR**: pytesseract (for screenshot analysis)

## Development Workflow

### Setup Commands

```bash
# Install all dependencies (run from root)
yarn install

# Backend setup (Windows)
cd packages/backend
python -m venv .venv
.\.venv\Scripts\Activate
pip install -r requirements.txt

# Backend setup (macOS/Linux)
cd packages/backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Running the Application

```bash
# Start both frontend and backend (from root)
yarn dev

# Or start individually:
yarn start:frontend  # Frontend on http://localhost:3000
yarn start:backend   # Backend on http://127.0.0.1:8000
```

### Build and Type Check

```bash
# Build frontend for production
yarn build

# Type check frontend
yarn typecheck
```

## Coding Standards

### Frontend
- Use **TypeScript** for all new files
- Follow **React Hooks** patterns - no class components
- Use **functional components** with TypeScript interfaces for props
- Leverage **Radix UI** components for accessibility
- Style with **Tailwind CSS** utility classes
- Use **lucide-react** for icons
- Keep components in `packages/frontend/src/components/`
- Keep pages in `packages/frontend/src/pages/`

### Backend
- Use **FastAPI** best practices with type hints
- Follow **PEP 8** Python style guidelines
- Use **Pydantic** models for request/response validation
- Keep ML models in `packages/backend/models/`
- Keep utility functions in `packages/backend/app/utils/`
- Use async/await for API endpoints where appropriate

### General Guidelines
- Write clear, descriptive commit messages
- Keep PRs focused and small
- Add comments only when necessary to explain complex logic
- Prioritize code readability and maintainability
- Follow existing patterns in the codebase

## Important Files

### Configuration
- Root: `package.json` - Yarn workspace configuration
- Frontend: `packages/frontend/package.json`, `packages/frontend/vite.config.ts`
- Backend: `packages/backend/requirements.txt`, `packages/backend/main.py`

### Environment Variables
- Frontend: Use `VITE_` prefix for environment variables (e.g., `VITE_API_URL`)
- Backend: Configure CORS origins and API settings in `.env`

### Key Components
- `packages/frontend/src/components/JobAnalyzer.tsx` - Main analysis interface
- `packages/frontend/src/components/TrustScoreDisplay.tsx` - Score visualization
- `packages/frontend/src/components/RedFlagsList.tsx` - Red flags display
- `packages/backend/main.py` - API entry point
- `packages/backend/app/utils/` - Data processing utilities

## API Integration

The frontend communicates with the backend via:
- Environment variable: `VITE_API_URL` (default: `http://127.0.0.1:8000`)
- Backend serves API docs at: `http://127.0.0.1:8000/docs`

## Testing

Currently, this repository does not have automated tests. When adding tests:
- Frontend: Use React Testing Library + Vitest
- Backend: Use pytest
- Keep test files in respective `tests/` directories

## Privacy and Ethics

- **Do not store user submissions** by default in the MVP
- Results are **advisory only** - not legally binding
- Keep code transparent and auditable
- Follow privacy-first principles

## Documentation

- Main README: `README.md` - Non-technical overview for stakeholders
- Technical README: `TechnicalReadMe.md` - Cross-platform setup guide
- Developer README: `devReadme.md` - Developer troubleshooting

## Target Audience

This application is designed for:
- International students and recent graduates
- Skilled newcomers searching for employment
- Community and settlement organizations

Keep the UI simple, non-technical, and accessible to users with limited technical background.

## Common Tasks

### Adding a new frontend component
1. Create file in `packages/frontend/src/components/`
2. Use TypeScript and functional component pattern
3. Style with Tailwind CSS
4. Export from the file and import where needed

### Adding a new API endpoint
1. Add route in `packages/backend/main.py` or create new router
2. Use Pydantic models for validation
3. Add type hints for parameters and return values
4. Update API documentation comments

### Updating dependencies
- Frontend: Add to `packages/frontend/package.json`, run `yarn install`
- Backend: Add to `packages/backend/requirements.txt`, run `pip install -r requirements.txt`

## Deployment Notes

- Frontend can be deployed to Vercel, Netlify, or similar
- Backend can be deployed to Render, AWS Lambda, or similar
- Ensure CORS is properly configured for production domains
- Set appropriate environment variables for production
