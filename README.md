# 🏎️ Multi-Track Car Racing with Deep Q-Learning

A comprehensive car racing simulation featuring both manual play and AI training capabilities. This project combines classic arcade-style racing with modern deep reinforcement learning, allowing you to either play manually or watch an AI agent learn to navigate various track designs.

## ✨ Features

### 🎮 Game Modes
- **Manual Play Mode**: Drive cars yourself with full control
- **AI Training Mode**: Watch Deep Q-Learning agents learn to race
- **AI Testing Mode**: Evaluate trained models on new tracks
- **Track Visualization**: Preview all available track designs

### 🏁 Track Variety
- **Oval Track**: Perfect for beginners, simple oval circuit
- **Rectangle Track**: Easy difficulty with rounded corners
- **L-Shape Track**: Medium difficulty with sharp turns
- **U-Shape Track**: Medium difficulty horseshoe design
- **Curved Track**: Hard difficulty with variable radius curves
- **Double Loop**: Expert level figure-8 style track
- **Test Track**: Simple circular track for validation

### 🤖 AI Features
- **Deep Q-Network (DQN)** with Double DQN and Dueling architecture
- **Curriculum Learning**: Progressive difficulty during training
- **Multi-track Training**: Agents learn across different track types
- **Advanced Sensors**: 15-point distance sensing system
- **Real-time Performance Metrics**: Speed, distance, collision detection

### 📊 Physics & Simulation
- **Realistic Car Physics**: Acceleration, friction, steering dynamics
- **Collision Detection**: Precise boundary checking
- **Sensor System**: Ray-casting for environmental awareness
- **Performance Tracking**: Lap times, distances, crash statistics

## 🚀 Quick Start

### Prerequisites
```bash
pip install pygame torch numpy
```

### Installation
1. Clone or download the project files
2. Ensure all Python files are in the same directory
3. Run the main application:

```bash
python main.py
```

## 🎯 How to Use

### Main Menu Options
1. **Manual Play Mode**: Choose a track and drive with keyboard controls
2. **Watch AI Training**: Observe the AI learning process in real-time
3. **Test Trained AI**: Load a trained model and watch it perform
4. **View All Tracks**: Preview all available track designs

### Manual Play Controls
- **Movement**: Arrow keys or WASD
  - ↑/W: Accelerate
  - ↓/S: Brake/Reverse
  - ←/A: Steer left
  - →/D: Steer right
- **Game Controls**:
  - R: Reset car position
  - T: Change track
  - SPACE: Pause/Resume
  - H: Toggle sensor visualization
  - ESC: Exit to menu

### AI Training
The AI uses a sophisticated Deep Q-Learning approach:
- **Input**: 24-dimensional state vector (15 sensors + car dynamics)
- **Output**: Steering and acceleration actions
- **Learning**: Experience replay with prioritized sampling
- **Architecture**: Dueling DQN with separate value and advantage streams

## 📁 Project Structure

```
├── main.py              # Entry point and main menu system
├── constants.py         # Global constants, colors, and configuration
├── utils.py            # Utility functions for geometry and smoothing
├── car.py              # Car class with physics and sensors
├── track.py            # Track generation and collision detection
├── environment.py      # RL environment wrapper
├── dqn_network.py      # Neural network architecture
├── dqn_agent.py        # DQN agent with training logic
├── manual_play.py      # Manual play mode and UI
├── training.py         # Training, testing, and visualization functions
└── models/             # Directory for saved AI models (auto-created)
```

## 🧠 AI Technical Details

### Deep Q-Network Architecture
- **Input Layer**: 24 features (sensor readings + car state)
- **Hidden Layers**: 3 layers with 256 neurons each
- **Output**: Dueling architecture with separate value and advantage streams
- **Activation**: ReLU with LayerNorm and Dropout
- **Optimizer**: Adam with gradient clipping

### State Representation
- 15 distance sensor readings (normalized)
- Current speed and average speed
- Car orientation (sin/cos of angle)
- Aggregated sensor data (front, left-right difference)
- Danger indicators and stuck detection

### Reward Function
- **Distance Progress**: Positive reward for forward movement
- **Collision Avoidance**: Penalties for getting too close to walls
- **Crash Penalty**: Large negative reward for collisions
- **Speed Regulation**: Penalties for excessive speed near obstacles
- **Completion Bonus**: Rewards for completing long episodes

### Training Features
- **Curriculum Learning**: Start with simple tracks, add complexity
- **Experience Replay**: Store and sample past experiences
- **Priority Replay**: Focus on high-impact experiences
- **Target Network**: Stable target for Q-learning updates
- **Epsilon Decay**: Gradually reduce exploration over time

## 🎨 Visual Features

### Real-time Display
- **Track Rendering**: Clean track boundaries with start/finish areas
- **Car Visualization**: Rotated car sprite with directional indicators
- **Sensor Overlay**: Color-coded distance sensors (red=danger, green=safe)
- **Performance HUD**: Speed, distance, lap times, and statistics

### Technical Dashboard (Manual Mode)
- **Physics Data**: Position, velocity, acceleration, G-forces
- **Sensor Readings**: Individual sensor values and aggregations
- **Car State**: Stuck detection, collision status, performance metrics
- **Real-time Updates**: All values update at 60 FPS

## 🏆 Performance Metrics

### Manual Play Statistics
- Best distance achieved per session
- Crash count and frequency
- Lap completion times
- Session duration tracking

### AI Training Metrics
- Episode rewards and convergence
- Training loss and network updates
- Exploration vs exploitation balance
- Multi-track performance comparison

## ⚙️ Configuration

### Customizable Parameters
- **Track Width**: Adjust difficulty by changing track boundaries
- **Car Physics**: Modify acceleration, top speed, friction values
- **AI Hyperparameters**: Learning rate, batch size, network architecture
- **Training Schedule**: Episode counts, curriculum timing

### Model Management
- **Auto-saving**: Best models saved during training
- **Checkpoints**: Regular training state preservation
- **Loading**: Resume training or test pre-trained models

## 🔧 Development Notes

### Code Organization
- **Modular Design**: Each component in separate files
- **Clean Interfaces**: Well-defined class interactions
- **No Comments**: Code structure is self-documenting
- **Python Best Practices**: Following PEP conventions

### Extension Points
- **New Tracks**: Add track types in `track.py`
- **Enhanced AI**: Modify network architecture in `dqn_network.py`
- **Additional Sensors**: Extend car sensing in `car.py`
- **Custom Rewards**: Adjust reward function in `environment.py`

## 🎓 Educational Value

This project demonstrates:
- **Reinforcement Learning**: Practical DQN implementation
- **Game Development**: Physics simulation and rendering
- **Neural Networks**: PyTorch-based deep learning
- **Software Architecture**: Clean, modular Python design
- **Real-time Systems**: 60 FPS game loop with AI integration

## 🔮 Future Enhancements

Potential improvements:
- **Multi-agent Racing**: Multiple cars competing simultaneously
- **Advanced AI**: PPO, A3C, or other RL algorithms
- **Track Editor**: Custom track creation tools
- **Online Leaderboards**: Compare performance across players
- **Physics Realism**: More sophisticated car dynamics
- **Visual Upgrades**: Enhanced graphics and animations

## 📝 License

This project is open source and available for educational and research purposes.

## 🤝 Contributing

Feel free to fork, modify, and improve this project. Areas for contribution:
- New track designs
- AI algorithm improvements
- Performance optimizations
- Visual enhancements
- Documentation updates

---

**Happy Racing! 🏁**