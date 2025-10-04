# MCP APP - Choose Your Own Adventure AI 🎮📚

A sophisticated, full-stack interactive storytelling application that leverages AI to create personalized adventure stories. Built with modern web technologies and integrated with the Model Context Protocol (MCP) for seamless natural language interactions through Gemini CLI.

## 🎥 Demo Video

**📹 Watch the Complete Demo** - Comprehensive walkthrough of the application features, MCP integration, and natural language interactions.

### 🎬 Watch the Demo Video

[![Watch Demo Video](https://img.shields.io/badge/🎥-Watch%20Demo%20Video-blue?style=for-the-badge&logo=video)](./MCP_app_recording.mp4)

**Click the button above to download and watch the demo video**

### 📱 Alternative Video Hosting Options:

#### Option 1: Loom (Recommended)
- Go to [Loom.com](https://loom.com)
- Upload your `MCP_app_recording.mp4`
- Get a shareable link
- Replace the button link above

#### Option 2: Vimeo
- Go to [Vimeo.com](https://vimeo.com)
- Upload your video
- Get embed link
- Update the button above

#### Option 3: Google Drive
- Upload to Google Drive
- Set sharing to "Anyone with link can view"
- Copy the shareable link
- Update the button above

#### Option 4: Dropbox
- Upload to Dropbox
- Create a shareable link
- Update the button above

### 📥 Direct Download
- **File**: [MCP_app_recording.mp4](./MCP_app_recording.mp4)
- **Size**: ~61 MB
- **Format**: MP4 (compatible with all devices)

### 🎯 What's Included in the Demo:
- ✅ **Story Creation**: Theme-based story generation
- ✅ **Interactive Gameplay**: Making choices and story progression  
- ✅ **MCP Integration**: Natural language commands through Gemini CLI
- ✅ **Frontend Interface**: React components and user experience
- ✅ **Backend API**: FastAPI endpoints and job processing
- ✅ **Real-time Updates**: Job status monitoring and story loading

### 💡 Quick Setup Instructions:
1. Choose one of the hosting options above
2. Upload your `MCP_app_recording.mp4` file
3. Get the shareable/embed link
4. Replace `./MCP_app_recording.mp4` in the button above with your new link
5. Commit and push the changes

*Note: These platforms provide better viewing experience than direct download and work well on GitHub.*

## 🌟 Key Features

### 🎯 Core Functionality
- **🧠 AI-Powered Story Generation**: Uses OpenAI's GPT models to create engaging, creative narratives
- **🎮 Interactive Storytelling**: Make choices that dynamically affect story direction and outcomes
- **🎨 Theme-Based Creation**: Generate stories from any theme (space adventure, medieval fantasy, detective mystery, etc.)
- **⚡ Real-time Processing**: Asynchronous story generation with comprehensive job status tracking
- **💾 Persistent Storage**: SQLite database for story persistence and retrieval
- **🔄 State Management**: Maintains game state across sessions with session tracking

### 🤖 Advanced MCP Integration
- **🗣️ Natural Language Interface**: Interact with the app using conversational commands through Gemini CLI
- **🔧 FastMCP Server**: Custom MCP server exposing comprehensive app functionality as callable tools
- **🌉 Seamless Bridge**: Intelligent translation between natural language and FastAPI backend
- **📊 State Tracking**: Maintains game state across MCP interactions
- **🎯 Context Awareness**: Remembers current story position and available options

## 🔄 Application Flow

```mermaid
flowchart TD
    A[User Input Theme] --> B[Frontend: StoryGenerator]
    B --> C[API: POST /stories/create]
    C --> D[Backend: Story Creation Job]
    D --> E[OpenAI: Generate Story]
    E --> F[Database: Save Story Structure]
    F --> G[Job Status: Completed]
    G --> H[Frontend: StoryGame Component]
    H --> I[User Makes Choice]
    I --> J[API: POST /stories/choice]
    J --> K[Backend: Process Choice]
    K --> L[OpenAI: Continue Story]
    L --> M[Database: Update Story]
    M --> N[Return Next Story Segment]
    N --> H
    
    %% MCP Integration Flow
    O[Gemini CLI] --> P[MCP Server]
    P --> Q[Natural Language Processing]
    Q --> R[MCP Tools]
    R --> S[create_story]
    R --> T[check_job_status]
    R --> U[get_story]
    R --> V[make_choice]
    R --> W[get_current_status]
    R --> X[list_available_options]
    
    S --> C
    T --> Y[Job Status Response]
    U --> Z[Story Data Response]
    V --> J
    W --> AA[Current Game State]
    X --> BB[Available Choices]
    
    %% Styling
    classDef frontend fill:#e1f5fe
    classDef backend fill:#f3e5f5
    classDef database fill:#e8f5e8
    classDef mcp fill:#fff3e0
    classDef ai fill:#fce4ec
    
    class A,B,H frontend
    class C,D,G,J,K,M,N backend
    class F database
    class O,P,Q,R,S,T,U,V,W,X mcp
    class E,L ai
```

## 🏗️ Technical Architecture

### 📱 Frontend Stack (React + Vite)
```
frontend/
├── src/
│   ├── components/
│   │   ├── StoryGenerator.jsx    # Theme input and story creation interface
│   │   ├── StoryGame.jsx         # Interactive story display and choice handling
│   │   ├── StoryLoader.jsx       # Story loading, navigation, and history
│   │   ├── LoadingStatus.jsx     # Real-time job status monitoring
│   │   └── ThemeInput.jsx        # Enhanced theme input component
│   ├── App.jsx                   # Main application component
│   ├── util.js                   # API configuration and utilities
│   ├── App.css                   # Application styling
│   └── index.css                 # Global styles
├── public/
│   └── vite.svg                  # Vite branding
├── package.json                  # Dependencies and scripts
├── vite.config.js               # Vite configuration
└── eslint.config.js             # ESLint configuration
```

**Frontend Technologies:**
- **React 19.1.0**: Latest React with concurrent features
- **Vite 6.3.5**: Fast build tool and development server
- **React Router DOM 7.6.0**: Client-side routing
- **Axios 1.9.0**: HTTP client for API communication
- **ESLint**: Code quality and consistency

### ⚙️ Backend Stack (FastAPI + SQLite)
```
backend/
├── main.py                       # FastAPI application entry point
├── mcp_server.py                 # Comprehensive MCP server implementation
├── core/
│   ├── config.py                 # Application configuration and settings
│   ├── models.py                 # SQLAlchemy database models
│   ├── prompts.py                # AI prompts for story generation
│   └── story_generator.py        # OpenAI integration and story logic
├── routers/
│   ├── story.py                  # Story-related API endpoints
│   └── job.py                    # Job status and management endpoints
├── db/
│   └── database.py               # Database connection and table creation
├── schemas/
│   ├── story.py                  # Pydantic schemas for story validation
│   └── job.py                    # Pydantic schemas for job validation
├── models/
│   ├── story.py                  # Story data models
│   └── job.py                    # Job data models
├── pyproject.toml                # Python project configuration
├── requirements.txt              # Python dependencies
├── uv.lock                       # UV lock file for dependency management
└── run_mcp_server.sh            # MCP server startup script
```

**Backend Technologies:**
- **FastAPI 0.115.12+**: Modern, fast web framework with automatic API documentation
- **SQLAlchemy 2.0.41+**: Advanced ORM for database operations
- **LangChain 0.3.25+**: Framework for LLM applications
- **LangChain OpenAI 0.3.18+**: OpenAI integration for LangChain
- **Uvicorn 0.34.2+**: ASGI server for FastAPI
- **Python-dotenv 1.1.0+**: Environment variable management
- **Pydantic**: Data validation and serialization

## 🚀 Installation & Setup

### 📋 Prerequisites
- **Python 3.13+** (as specified in pyproject.toml)
- **Node.js 16+** (for frontend development)
- **OpenAI API Key** (for story generation)
- **Git** (for version control)

### 🔧 Installation Steps

1. **Clone the Repository**
   ```bash
   git clone <your-repository-url>
   cd MCP\ APP
   ```

2. **Backend Setup**
   ```bash
   cd backend
   
   # Create virtual environment
   python -m venv venv
   
   # Activate virtual environment
   # Windows:
   venv\Scripts\activate
   # macOS/Linux:
   source venv/bin/activate
   
   # Install dependencies using pip or uv
   pip install -r requirements.txt
   # OR if using uv:
   uv pip install -r requirements.txt
   ```

3. **Environment Configuration**
   ```bash
   # Create .env file in backend directory
   cat > .env << EOF
   DATABASE_URL=sqlite:///./databse.db
   API_PREFIX=/api
   DEBUG=True
   ALLOWED_ORIGINS=http://localhost:3000,http://localhost:5173,https://localhost:3000,https://localhost:5173
   OPENAI_API_KEY=your_openai_api_key_here
   EOF
   ```

4. **Frontend Setup**
   ```bash
   cd ../frontend
   npm install
   ```

### 🏃‍♂️ Running the Application

1. **Start Backend Server**
   ```bash
   cd backend
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   python main.py
   ```
   - Backend available at: `http://localhost:8000`
   - API Documentation: `http://localhost:8000/docs`
   - ReDoc Documentation: `http://localhost:8000/redoc`

2. **Start Frontend Development Server**
   ```bash
   cd frontend
   npm run dev
   ```
   - Frontend available at: `http://localhost:5173`

## 🤖 MCP Integration Deep Dive

### 🔍 What is MCP?
The Model Context Protocol (MCP) is a standardized protocol for connecting AI assistants with external tools and data sources. Our implementation creates a bridge between natural language commands and the application's functionality.

### 🛠️ MCP Server Architecture

The MCP server (`mcp_server.py`) provides:

- **State Management**: Tracks current story, node position, and session data
- **Tool Exposure**: Exposes 6 comprehensive tools for natural language interaction
- **Error Handling**: Robust error handling with detailed error messages
- **Session Persistence**: Maintains game state across interactions

### 🔧 MCP Server Setup

1. **Install FastMCP**
   ```bash
   cd backend
   source venv/bin/activate
   pip install fastmcp
   ```

2. **Configure Gemini CLI**
   
   Update your `~/.gemini/settings.json`:
   ```json
   {
     "theme": "Atom One",
     "selectedAuthType": "oauth-personal",
     "mcpServers": {
       "adventure-game": {
         "command": "/path/to/MCP APP/backend/run_mcp_server.sh",
         "args": [],
         "env": {}
       }
     }
   }
   ```

3. **Make Script Executable**
   ```bash
   chmod +x backend/run_mcp_server.sh
   ```

### 🛠️ Available MCP Tools

| Tool | Description | Parameters | Example Usage |
|------|-------------|------------|---------------|
| `create_story` | Generate new story with theme | `theme: str` | "Create a story about space pirates" |
| `check_job_status` | Check story generation progress | `job_id: Optional[str]` | "What's the status of my story?" |
| `get_story` | Retrieve complete story for gameplay | `story_id: Optional[int]` | "Load my current story" |
| `make_choice` | Make interactive story choice | `choice_text: str` | "Choose the first option" |
| `get_current_status` | Get current game state | None | "What's my current position?" |
| `list_available_options` | List all available choices | None | "What choices do I have?" |

### 💬 Natural Language Examples

Once connected to Gemini CLI, you can use conversational commands:

**Story Creation:**
- "Create a new adventure story about space exploration"
- "Generate a mystery story set in Victorian London"
- "Make a fantasy story about dragons and magic"

**Gameplay:**
- "What's the status of my story?"
- "Load my current story"
- "What choices do I have?"
- "I want to choose the first option"
- "Choose the path that leads to the castle"

**Status Checking:**
- "What's my current position in the story?"
- "Is my story ready yet?"
- "Show me the complete story we just created"

## 🛠️ API Reference

### 📚 Story Management Endpoints

| Method | Endpoint | Description | Request Body | Response |
|--------|----------|-------------|--------------|----------|
| `POST` | `/api/stories/create` | Create new story | `{"theme": "string"}` | Job information |
| `GET` | `/api/stories/{story_id}/complete` | Get complete story | None | Full story data |
| `POST` | `/api/stories/{story_id}/choice` | Make story choice | `{"choice": "string"}` | Next story segment |

### ⚙️ Job Management Endpoints

| Method | Endpoint | Description | Response |
|--------|----------|-------------|----------|
| `GET` | `/api/jobs/{job_id}` | Get job status | Job status and details |

### 📊 Data Models

**Story Structure:**
```json
{
  "id": "integer",
  "title": "string",
  "theme": "string",
  "created_at": "datetime",
  "root_node": {
    "id": "integer",
    "content": "string",
    "is_ending": "boolean",
    "options": [
      {
        "text": "string",
        "next_node_id": "integer"
      }
    ]
  },
  "all_nodes": {
    "node_id": {
      "content": "string",
      "is_ending": "boolean",
      "options": "array"
    }
  }
}
```

## 🎯 How It Works - Deep Dive

### 🔄 Story Generation Process

1. **Theme Input**: User provides a theme (e.g., "space adventure")
2. **AI Processing**: OpenAI GPT generates initial story setup with multiple paths
3. **Database Storage**: Story structure saved to SQLite database
4. **Job Tracking**: Asynchronous job system tracks generation progress
5. **Interactive Play**: User makes choices that dynamically continue the narrative

### 🧠 AI Integration Details

- **Model**: Uses OpenAI's GPT models for story generation
- **Prompt Engineering**: Custom prompts ensure consistent story structure and quality
- **Narrative Coherence**: Maintains story consistency across multiple segments
- **Dynamic Branching**: Creates multiple story paths based on user choices
- **Ending Detection**: Identifies natural story conclusions

### 💾 Database Schema

**Stories Table:**
- `id`: Primary key
- `title`: Generated story title
- `theme`: User-provided theme
- `created_at`: Timestamp
- `root_node_id`: Reference to starting node

**Story Nodes Table:**
- `id`: Primary key
- `story_id`: Foreign key to stories
- `content`: Story text content
- `is_ending`: Boolean flag for story endings
- `is_winning_ending`: Boolean flag for positive endings

**Story Options Table:**
- `id`: Primary key
- `node_id`: Foreign key to story nodes
- `text`: Choice description
- `next_node_id`: Foreign key to next node

**Jobs Table:**
- `id`: Primary key (UUID)
- `status`: Job status (pending, processing, completed, failed)
- `story_id`: Foreign key to generated story
- `theme`: Original theme
- `created_at`: Job creation timestamp
- `completed_at`: Job completion timestamp
- `error`: Error message if failed

## 🔧 Configuration & Environment

### 🌍 Environment Variables

| Variable | Description | Default Value | Required |
|----------|-------------|---------------|----------|
| `DATABASE_URL` | SQLite database connection string | `sqlite:///./databse.db` | No |
| `API_PREFIX` | API route prefix | `/api` | No |
| `DEBUG` | Enable debug mode | `True` | No |
| `ALLOWED_ORIGINS` | CORS allowed origins | localhost variants | No |
| `OPENAI_API_KEY` | OpenAI API key for story generation | None | **Yes** |

### 🔒 CORS Configuration

The backend is configured to allow requests from:
- `http://localhost:3000` (React default port)
- `http://localhost:5173` (Vite default port)
- `https://localhost:3000` (HTTPS variant)
- `https://localhost:5173` (HTTPS variant)

### 📁 File Structure Overview

```
MCP APP/
├── backend/                    # FastAPI backend
│   ├── core/                  # Core application logic
│   ├── db/                    # Database configuration
│   ├── models/                # Data models
│   ├── routers/               # API route handlers
│   ├── schemas/               # Pydantic schemas
│   ├── main.py                # Application entry point
│   ├── mcp_server.py          # MCP server implementation
│   └── requirements.txt       # Python dependencies
├── frontend/                  # React frontend
│   ├── src/                   # Source code
│   ├── public/                # Static assets
│   └── package.json           # Node.js dependencies
├── mcp_config.json           # MCP configuration
├── mcp_requirements.txt      # MCP-specific dependencies
├── setup_mcp.sh              # MCP setup script
└── README.md                  # This file
```

## 🚀 Deployment Guide

### ☁️ Backend Deployment

**Production Considerations:**
- Replace SQLite with PostgreSQL for better performance and scalability
- Use environment-specific configuration files
- Implement proper logging and monitoring
- Set up reverse proxy (nginx) for production
- Use process manager (PM2, systemd) for process management

**Docker Deployment:**
```dockerfile
FROM python:3.13-slim
WORKDIR /app
COPY backend/requirements.txt .
RUN pip install -r requirements.txt
COPY backend/ .
EXPOSE 8000
CMD ["python", "main.py"]
```

### 🌐 Frontend Deployment

**Build Process:**
```bash
cd frontend
npm run build
```

**Deployment Options:**
- Static hosting (Netlify, Vercel, GitHub Pages)
- CDN deployment
- Container deployment with nginx

### 🔧 Production Environment Variables

```bash
DATABASE_URL=postgresql://user:password@localhost:5432/adventure_db
API_PREFIX=/api
DEBUG=False
ALLOWED_ORIGINS=https://yourdomain.com,https://www.yourdomain.com
OPENAI_API_KEY=your_production_openai_key
```

## 🧪 Testing

### 🔬 Backend Testing
```bash
cd backend
source venv/bin/activate
pytest tests/
```

### 🎨 Frontend Testing
```bash
cd frontend
npm test
```

### 🧪 MCP Testing
Test MCP integration by connecting to Gemini CLI and using natural language commands.

## 🤝 Contributing

### 📝 Development Workflow

1. **Fork the Repository**
   ```bash
   git clone <your-fork-url>
   cd MCP\ APP
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make Changes**
   - Follow existing code style
   - Add appropriate tests
   - Update documentation

4. **Commit Changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```

5. **Push and Create Pull Request**
   ```bash
   git push origin feature/amazing-feature
   ```

### 📋 Code Standards

- **Python**: Follow PEP 8 style guide
- **JavaScript**: Use ESLint configuration
- **Documentation**: Update README for new features
- **Testing**: Add tests for new functionality
- **Type Hints**: Use type hints in Python code

## 🐛 Troubleshooting

### Common Issues

**Backend Issues:**
- **Port 8000 already in use**: Change port in `main.py` or kill existing process
- **Database connection errors**: Check `DATABASE_URL` in `.env`
- **OpenAI API errors**: Verify `OPENAI_API_KEY` is correct and has credits

**Frontend Issues:**
- **Port 5173 already in use**: Vite will automatically use next available port
- **API connection errors**: Ensure backend is running on correct port
- **Build errors**: Clear `node_modules` and reinstall dependencies

**MCP Issues:**
- **MCP server not starting**: Check Python path in `mcp_config.json`
- **Tools not available**: Verify MCP server is running and connected
- **State not persisting**: Check MCP server logs for errors

### 🔍 Debug Mode

Enable debug mode by setting `DEBUG=True` in your `.env` file. This provides:
- Detailed error messages
- Request/response logging
- Database query logging
- MCP server debug output

## 📚 Additional Resources

### 📖 Documentation Links
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [React Documentation](https://reactjs.org/docs/)
- [Vite Documentation](https://vitejs.dev/)
- [FastMCP Documentation](https://fastmcp.com/)
- [OpenAI API Documentation](https://platform.openai.com/docs)

### 🎓 Learning Resources
- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [SQLAlchemy Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
- [React Router Guide](https://reactrouter.com/en/main)

## 📝 License

**© 2025 Sufi Hassan Asim. All rights reserved.**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

For inquiries, please contact: [hassanasim337@gmail.com](mailto:hassanasim337@gmail.com)

## 👨‍💻 Author

**Sufi Hassan Asim**
- 📧 Email: [hassanasim337@gmail.com](mailto:hassanasim337@gmail.com)
- 🎯 Creator of MCP APP - Choose Your Own Adventure AI
- 📅 All rights reserved © 2025

## 🙏 Acknowledgments

- **FastAPI** - Modern, fast web framework for building APIs
- **React** - JavaScript library for building user interfaces
- **Vite** - Next generation frontend tooling
- **FastMCP** - Model Context Protocol server implementation
- **OpenAI** - AI-powered story generation capabilities
- **SQLAlchemy** - Python SQL toolkit and ORM
- **LangChain** - Framework for developing LLM applications

## 📞 Support & Community

### 🆘 Getting Help

1. **Check Documentation**: Review this README and inline code comments
2. **Search Issues**: Look through existing GitHub issues
3. **Create Issue**: Submit detailed bug reports or feature requests
4. **Community**: Join discussions in project forums

### 🐛 Reporting Bugs

When reporting bugs, please include:
- **Environment**: OS, Python version, Node.js version
- **Steps to Reproduce**: Detailed steps to recreate the issue
- **Expected Behavior**: What should happen
- **Actual Behavior**: What actually happens
- **Error Messages**: Full error logs and stack traces
- **Screenshots**: Visual evidence if applicable

### 💡 Feature Requests

For feature requests, please provide:
- **Use Case**: Why this feature would be valuable
- **Proposed Solution**: How you envision it working
- **Alternatives**: Other approaches you've considered
- **Additional Context**: Any relevant background information

---

**🎭 Happy Storytelling!** ✨

*Built with ❤️ for interactive AI storytelling*
