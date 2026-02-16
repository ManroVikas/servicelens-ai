# ServiceLens Analytics Dashboard (Plotly Dash)

<p align="center">
  <strong>Enterprise-Grade SLA Analytics with AI-Powered Automation</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Dash-2.14-blue.svg" alt="Dash"/>
  <img src="https://img.shields.io/badge/Python-3.11-green.svg" alt="Python"/>
  <img src="https://img.shields.io/badge/Docker-Ready-blue.svg" alt="Docker"/>
  <img src="https://img.shields.io/badge/AI-Powered-purple.svg" alt="AI"/>
</p>

---

## 🚀 Features

- **High Performance**: Built with Plotly Dash for efficient, callback-based updates
- **Modular Architecture**: Separated layouts, callbacks, and utilities for maintainability
- **Client-Side Data Storage**: Uses `dcc.Store` for efficient data management
- **Dynamic Column Mapping**: Dropdowns auto-populate from uploaded file headers
- **Professional UI**: Bootstrap LUX theme with custom styling
- **AI Integration**: API keys loaded from `.env` file (no manual entry needed)

---

## 📁 Project Structure

```
servicelens_dash/
├── app.py              # Main application entry point
├── layouts.py          # UI components and page layouts
├── callbacks.py        # All Dash callbacks
├── config.py           # Configuration and constants
├── utils/
│   ├── __init__.py
│   ├── data_processing.py   # Data transformation functions
│   ├── charts.py            # Chart generation functions
│   └── ai_provider.py       # AI integration
├── assets/
│   └── styles.css      # Custom CSS styling
├── .env.example        # Environment variables template
├── requirements.txt    # Python dependencies
├── Dockerfile          # Container configuration
└── README.md
```

---

## 🔧 Installation

### Option 1: Local Development

```bash
# Clone/download the project
cd servicelens_dash

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\\Scripts\\activate   # Windows

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY

# Run the application
python app.py
```

### Option 2: Docker

```bash
# Build the image
docker build -t servicelens-dash .

# Run with environment file
docker run -d -p 8050:8050 --env-file .env --name servicelens servicelens-dash

# Or run with inline env var
docker run -d -p 8050:8050 -e OPENAI_API_KEY=sk-your-key --name servicelens servicelens-dash
```

---

## ⚙️ Configuration

### Environment Variables (.env)

```env
# OpenAI API Key (for AI recommendations)
OPENAI_API_KEY=sk-your-openai-api-key

# AWS Bedrock (alternative)
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=us-east-1

# Application Settings
DEBUG=False
PORT=8050
SECRET_KEY=your-secret-key

# SLA Thresholds (hours)
SLA_CRITICAL=4
SLA_HIGH=8
SLA_MEDIUM=24
SLA_LOW=72
```

---

## 📊 Usage

1. **Access**: Open `http://localhost:8050`

2. **Upload Data**: 
   - Go to Configuration page
   - Upload CSV or Excel file

3. **Map Columns**:
   - Select matching columns from dropdowns
   - All required fields must be mapped

4. **Configure SLA**:
   - Set thresholds for each priority

5. **Process**:
   - Click "Confirm Mapping & Process Data"

6. **View Analytics**:
   - Navigate to Analytics Dashboard
   - All charts update based on processed data

7. **AI Features** (optional):
   - Enable AI Mode in sidebar
   - Test connection (uses API key from .env)
   - Generate recommendations for patterns

---

## 🆚 Key Differences from Streamlit Version

| Feature | Streamlit | Plotly Dash |
|---------|-----------|-------------|
| Re-runs | Full page on any change | Only affected callbacks |
| Data Storage | Session state | `dcc.Store` (client-side) |
| Mapping Update | Immediate | On "Confirm" button click |
| Architecture | Single file | Multi-file modular |
| API Key Entry | Manual input | Loaded from .env |
| Production | Limited | Gunicorn-ready |

---

## 🔑 AI Integration

The AI features use your API key from the `.env` file:

- **No manual entry required** - key is loaded automatically
- **Test Connection** button verifies the key works
- Only anonymized data (patterns, counts) sent to AI
- Privacy-first: No PII ever transmitted

---

## 📦 Sample Data Format

```csv
ticket_id,created_date,resolved_date,priority,assigned_team,assignee_name,description
INC001,2024-01-15 08:30:00,2024-01-15 10:45:00,High,Network Team,John Smith,VPN issues
INC002,2024-01-15 09:00:00,2024-01-16 14:30:00,Medium,Desktop Support,Jane Doe,Email sync
```

---

## 🐳 Docker Commands

```bash
# Build
docker build -t servicelens-dash .

# Run (with .env file)
docker run -d -p 8050:8050 --env-file .env --name servicelens servicelens-dash

# View logs
docker logs -f servicelens

# Stop
docker stop servicelens

# Remove
docker rm servicelens
```

---

## 📄 License

MIT License

---

<p align="center">
  <strong>ServiceLens Dash</strong><br>
  Enterprise SLA Analytics • AI-Powered Automation
</p>
