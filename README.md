# ROS-HARi: Human-AI-Robot interface

ROS-LLM is an advanced framework that combines the power of Large Language Models (LLMs) with ROS 2 to create a more natural and intuitive human-robot interaction system. This project extends the original ROSGPT work by adding real-time voice interaction capabilities, making it easier for users to control robots through natural language and voice commands.

## Key Features

- **Real-time Voice Control**: Direct voice commands for robot control using Google's Web Speech API
- **Two-way Conversation**: Interactive voice feedback and command clarification
- **Natural Language Processing**: Integration with ChatGPT for complex command understanding
- **Multiple Robot Support**: Compatible with Turtlesim and Turtlebot3
- **REST API Interface**: Flexible integration options for different applications

## Reference Paper

[![DOI](https://img.shields.io/badge/DOI-10.20944%2Fpreprints202304.0827.v2-blue)](https://www.preprints.org/manuscript/202304.0827/v2)

**Original Author**: Anis Koubaa

**Citation**: Koubaa, A. (2023). ROSGPT: Next-Generation Human-Robot Interaction with ChatGPT and ROS. Preprints.org, 2023, 2023040827.
https://www.preprints.org/manuscript/202304.0827/v2

**BibTeX Citation**:

```bibtex
@article{koubaa2023rosgpt,
  title={ROSGPT: Next-Generation Human-Robot Interaction with ChatGPT and ROS},
  author={Koubaa, Anis},
  journal={Preprints.org},
  year={2023},
  volume={2023},
  pages={2023040827},
  doi={10.20944/preprints202304.0827.v2}
}
```

## New Features

### Voice-Controlled Turtlebot

The new voice control system includes:

- **Real-time Speech Recognition**: Using Google's Web Speech API for accurate voice command recognition
- **Text-to-Speech Feedback**: Immediate voice responses for command confirmation and clarification
- **Command Clarification**: Interactive dialogue when commands are ambiguous
- **Natural Movement Commands**: Support for intuitive voice commands like "move forward", "turn left", etc.
- **Speed Control**: Voice commands for adjusting robot speed
- **Position Control**: Commands for specific positions and drawing patterns

## Installation

1. Clone the repository:
```bash
git clone https://github.com/nikolasdoan/ROS-LLM.git
cd ROS-LLM
```

2. Install system dependencies:
```bash
sudo apt-get update
sudo apt-get install -y \
    python3-pip \
    python3-espeak \
    libespeak1 \
    ros-humble-turtlesim* \
    portaudio19-dev \
    python3-pyaudio
```

3. Install Python dependencies:
```bash
cd rosgpt
pip3 install -r requirements.txt
```

4. Set up your OpenAI API key (for ChatGPT integration):
```bash
echo 'export OPENAI_API_KEY=your_api_key' >> ~/.bashrc
source ~/.bashrc
```

5. Build the ROS 2 package:
```bash
cd /path/to/ROS-LLM
colcon build --packages-select rosgpt
source install/setup.bash
```

## Usage

### Voice Control Mode

1. Start the turtlesim:
```bash
ros2 run turtlesim turtlesim_node
```

2. Run the voice-controlled turtlebot:
```bash
ros2 run rosgpt voice_controlled_turtlebot
```

3. Available voice commands:
   - Movement: "forward", "backward", "turn left", "turn right", "stop"
   - Speed: "speed up", "slow down"
   - Position: "go home", "draw circle", "draw square"

### Text Command Mode

1. Start the ROSGPT server:
```bash
ros2 run rosgpt rosgpt
```

2. Run the turtlesim:
```bash
ros2 run turtlesim turtlesim_node
```

3. Run the command parser:
```bash
ros2 run rosgpt rosgptparser_turtlesim
```

4. Run the client:
```bash
ros2 run rosgpt rosgpt_client_node
```

## Project Structure

- **voice_controlled_turtlebot.py**: Main voice control implementation
- **rosgpt.py**: ChatGPT integration server
- **rosgptparser_turtlesim.py**: Command parser for Turtlesim
- **rosgptparser_tb3_nav.py**: Command parser for Turtlebot3
- **rosgpt_client_node.py**: ROS 2 client node
- **rosgpt_client.py**: REST API client

## License

This project is licensed under the Creative Commons Attribution-NonCommercial 4.0 International License. You are free to use, share, and adapt this material for non-commercial purposes, as long as you provide attribution to the original author(s) and the source.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## Acknowledgments

- Original ROSGPT work by Anis Koubaa
- Google Web Speech API for voice recognition
- ROS 2 community for the excellent robotics framework
