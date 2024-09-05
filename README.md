Certainly! Here’s a revised README focusing on the company MLAI and a model named Abi (or Abbey):

---

# MLAI Open WebUI & Deployment Container 👋

![GitHub stars](https://img.shields.io/github/stars/open-webui/open-webui?style=social)
![GitHub forks](https://img.shields.io/github/forks/open-webui/open-webui?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/open-webui/open-webui?style=social)
![GitHub repo size](https://img.shields.io/github/repo-size/open-webui/open-webui)
![GitHub language count](https://img.shields.io/github/languages/count/open-webui/open-webui)
![GitHub top language](https://img.shields.io/github/languages/top/open-webui/open-webui)
![GitHub last commit](https://img.shields.io/github/last-commit/open-webui/open-webui?color=red)
![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Follama-webui%2Follama-wbui&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)
[![Discord](https://img.shields.io/badge/Discord-MLAI-blue?logo=discord&logoColor=white)](https://discord.gg/5rJgQTnV4s)
[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/tjbck)

## Overview

Welcome to the MLAI Open WebUI, a sophisticated, extensible WebUI designed for seamless operation with the Abi model (also known as Abbey) by MLAI. This WebUI is perfect for organizations and individuals who want to leverage powerful language models offline. 

For comprehensive details, check out our [MLAI Open WebUI Documentation](https://docs.openwebui.com/).

![Open WebUI Demo](./demo.gif)

## Key Features ⭐

- **Easy Deployment**: Quickly set up using Docker or Kubernetes. Supports configurations with or without GPU acceleration.

- **Abi Model Integration**: Directly integrate the Abi model for advanced conversational capabilities. Configure your API settings to link with MLAI’s services or other compatible endpoints.

- **Custom Pipelines**: Enhance your WebUI with custom logic and Python libraries using our [Pipelines Plugin Framework](https://github.com/open-webui/pipelines). Add features like function calling, usage monitoring, and multilingual support with ease.

- **Responsive Design**: Access your WebUI on desktops, laptops, and mobile devices with a seamless user experience.

- **Progressive Web App (PWA)**: Enjoy a native app-like experience on mobile devices, with offline access and a smooth interface.

- **Markdown and LaTeX Support**: Utilize full Markdown and LaTeX support for enriched interactions.

- **Voice/Video Communication**: Integrate hands-free voice and video calls directly within the chat environment.

- **Model Builder**: Create and manage Abi models via the WebUI. Customize chat interactions and import models efficiently.

- **Python Function Integration**: Add and use your own Python functions within the WebUI’s code editor.

- **Local RAG Integration**: Implement Retrieval Augmented Generation (RAG) for document interactions. Load documents into the chat or add them to your library for easy access.

- **Web Search and Browsing**: Perform web searches and integrate web content into your chats for enhanced interaction.

- **Image Generation**: Incorporate image generation tools like AUTOMATIC1111 API, ComfyUI, or OpenAI’s DALL-E.

- **Multi-Model Conversations**: Engage with multiple models simultaneously to leverage their unique strengths.

- **Role-Based Access Control (RBAC)**: Secure your setup with role-based permissions to control access effectively.

- **Multilingual Support**: Use Open WebUI in various languages and contribute to expanding our language options.

- **Regular Updates**: Stay updated with new features and improvements through continuous updates.

Explore more features in our [MLAI Open WebUI documentation](https://docs.openwebui.com/features).

## Getting Started 🚀

### Quick Start with Docker 🐳

> **Note:** Ensure you include `-v open-webui:/app/backend/data` in your Docker command to preserve data.

#### Default Installation

- **With Local Abi Model**:

  ```bash
  docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

- **With Remote Abi Model**:

  ```bash
  docker run -d -p 3000:8080 -e ABI_BASE_URL=https://example.com -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

- **With GPU Support**:

  ```bash
  docker run -d -p 3000:8080 --gpus all --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:cuda
  ```

#### Abi Model Only

  ```bash
  docker run -d -p 3000:8080 -e ABI_API_KEY=your_secret_key -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

#### Bundled Abi Model Support

- **With GPU**:

  ```bash
  docker run -d -p 3000:8080 --gpus=all -v abi:/root/.abi -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:abi
  ```

- **Without GPU**:

  ```bash
  docker run -d -p 3000:8080 -v abi:/root/.abi -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:abi
  ```

Access Open WebUI at [http://localhost:3000](http://localhost:3000). Enjoy! 😄

### Alternative Installation Methods

For non-Docker options and additional installation methods, refer to our [MLAI Open WebUI Documentation](https://docs.openwebui.com/getting-started/).

### Troubleshooting

For connection issues, consult our [Troubleshooting Guide](https://docs.openwebui.com/troubleshooting/) or join our [Discord community](https://discord.gg/5rJgQTnV4s).

**Connection Error Solution:**

Use the `--network=host` flag if you encounter connection issues:

```bash
docker run -d --network=host -v open-webui:/app/backend/data -e ABI_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

### Keeping Your Installation Updated

Update your Docker installation with [Watchtower](https://containrrr.dev/watchtower/):

```bash
docker run --rm --volume /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --run-once open-webui
```

Replace `open-webui` with your container name if different.

### Using the Dev Branch 🌙

For the latest features and updates (with possible instability), use the `:dev` tag:

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data --name open-webui --add-host=host.docker.internal:host-gateway --restart always ghcr.io/open-webui/open-webui:dev
```

## Future Plans 🌟

Check out our upcoming features and roadmap in the [MLAI Open WebUI Documentation](https://docs.openwebui.com/roadmap/).

## Supporters ✨

A heartfelt thanks to all our supporters and mentors who make this project possible.

## License 📜

This project is licensed under the [MIT License](LICENSE). See the [LICENSE](LICENSE) file for details.

## Support 💬

For any questions or support, please open an issue or join our [MLAI Discord community](https://discord.gg/5rJgQTnV4s).

## Star History

<a href="https://star-history.com/#open-webui/open-webui&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date" />
  </picture>
</a>

---

Created by the MLAI team - Let's make the Open WebUI even better together! 💪
