<p align="center">
    <h1 align="center">📱 AK - WhatsApp AI Agent 📱</h1>
    <h3 align="center">Turning the Turing Test into a WhatsApp Agent</h3>
</p>

## Overview

Meet **AK**, a WhatsApp agent. This implementation demonstrates how artificial intelligence can create engaging, natural conversations through a familiar messaging platform. While not fully sentient, AK showcases the current capabilities of modern AI technologies in a practical application.

AK features a comprehensive set of capabilities:

* Bidirectional WhatsApp messaging integration
* Speech recognition for processing voice messages
* Computer vision for image analysis and understanding
* Text-to-speech synthesis for natural voice responses
* Contextual memory for maintaining conversation history
* Image generation based on textual descriptions
* Simulated activities based on scheduling algorithms

This project represents a practical implementation of theoretical AI concepts, creating an agent that can pass a modern interpretation of the Turing Test through a messaging platform.

[![Watch the Demo Video](http://www.youtube.com/watch?v=fpzGUJKOL6M&t=17)](https://www.youtube.com/watch?v=fpzGUJKOL6M)

## Technical Implementation

<img width="966" height="731" alt="Screenshot 2025-07-15 at 12 26 18 AM" src="https://github.com/user-attachments/assets/f931dd0a-3ad2-41ca-b9d2-7dafdd5240d7" />


<img width="330" alt="Screenshot 2025-04-28 at 10 47 59 AM" src="https://github.com/user-attachments/assets/ae66222a-971f-4230-aa90-d9e1dc2f532a" />

<img width="332" alt="Screenshot 2025-04-28 at 10 48 14 AM" src="https://github.com/user-attachments/assets/8637f607-b940-468d-8d13-f7bbeca2a7cc" />

### System Requirements

- Python 3.12
- Docker Desktop
- API keys for:
  - Groq (LLM and vision models)
  - ElevenLabs (speech synthesis)
  - Together AI (image generation)
  - Qdrant (vector database)
  - WhatsApp Business API (for production deployment)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Bharath0726/Ak_Whatsapp_Agent.git
cd ak-whatsapp-agent-course
```

2. Configure the Python environment with UV:
```bash
uv venv
source .venv/bin/activate  # On Windows, use: .venv\Scripts\activate
uv pip install -e .
```

3. Configure environment variables:
```bash
cp .env.template .env
```

4. Populate the `.env` file with appropriate API credentials:
```
GROQ_API_KEY="api-key-here"
ELEVENLABS_API_KEY="api-key-here"
ELEVENLABS_VOICE_ID="voice-id-here"
TOGETHER_API_KEY="api-key-here"
QDRANT_URL="qdrant-url-here"
QDRANT_API_KEY="api-key-here"
WHATSAPP_PHONE_NUMBER_ID="id-here"
WHATSAPP_TOKEN="token-here"
WHATSAPP_VERIFY_TOKEN="AKAGENT"
```

For detailed setup instructions, refer to the GETTING_STARTED.md documentation in the docs directory.

### Execution

The project utilizes Docker containers for seamless deployment:

```bash
# Build and deploy all services (database, UI, WhatsApp integration)
make ak-run

# Terminate services
make ak-stop

# Remove containers and clear storage
make ak-delete
```

After initialization, access the web interface at http://localhost:8000 to interact with AK directly.

## Architecture

AK employs a sophisticated modular architecture:

- **LangGraph Framework**: Orchestrates conversational workflows and decision trees
- **Large Language Models**: Llama 3.3 (70B parameters) for text generation
- **Vision Language Models**: Llama 3.2 Vision for image understanding and analysis
- **Vector Database**: Qdrant for similarity search and long-term memory persistence
- **Speech Processing**: Whisper for speech-to-text and ElevenLabs for text-to-speech
- **Image Generation**: FLUX models via Together AI for creating visual content
- **Web Interface**: Chainlit for interactive UI components
- **API Integration**: FastAPI for WhatsApp webhook endpoints

The system implements a directed acyclic graph (DAG) design pattern for message processing, with specialized nodes for:
- Memory extraction
- Context injection
- Response routing
- Content generation
- Multi-modal synthesis

## Customization Capabilities

The system allows for significant customization:

1. Character behavior and knowledge via `src/ai_companion/prompts/character_card.py`
2. Workflow modification through `src/ai_companion/graph/graph.py`
3. Integration of additional external tools and services
4. Configuration adjustments via environment variables

## Cloud Deployment

For scalable deployment, AK supports Google Cloud Run:

1. Create a Google Cloud project
2. Enable necessary API services
3. Configure secret management for API keys
4. Deploy using the provided Cloud Build configuration

Comprehensive deployment instructions are available in the gcp_setup.md documentation.

## Evaluation Metrics

AK's performance can be evaluated on several dimensions:

- **Response Quality**: Coherence and relevance of generated text
- **Vision Capabilities**: Accuracy of image recognition and description
- **Speech Quality**: Naturalness of synthesized voice responses
- **Memory Persistence**: Ability to recall previous conversation context
- **User Engagement**: Conversation length and user satisfaction

## Resource Considerations

This project is optimized for cost-efficiency:

- Free service tiers from Groq, ElevenLabs, Qdrant Cloud, and Together AI are sufficient for testing
- Local deployment requires minimal computational resources
- Cloud deployment costs approximately $2-5/month for moderate usage

## Troubleshooting

Common technical issues and resolution steps:

- Docker connectivity: Restart Docker Desktop service
- API authentication: Verify credential validity in environment variables
- WhatsApp connectivity: Ensure webhook URL is publicly accessible
- Response generation: Examine container logs using `docker-compose logs`

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

This project builds upon several open-source technologies and AI models. Special thanks to the developers of LangGraph, Chainlit, and the various AI services that make this possible.
