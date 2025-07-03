# Network Aquarium Project - RE203

## Copyright Notice
© 2025 Derache C., François M., Maulard J., Larragueta C. All rights reserved.

This project was developed as part of the RE203 Networks course by a team of five students who contributed equally to all aspects of the development. The project was originally developed on a private institutional Git repository (Thor forge) and has been migrated to this public repository, which explains the single commit history. No part of this project may be reproduced, distributed, or transmitted in any form or by any means without the prior written permission of the authors.

## Description
This project simulates a centralized network aquarium where fish move according to predefined mobility patterns. The system follows the Model-View-Controller (MVC) architecture with a centralized controller managing fish positions and multiple display clients showing the aquarium state.

The project consists of:
- **Controller Program** (Server): A C-based server that manages the aquarium topology, fish positions, and mobility algorithms
- **Display Program** (Client): A Java-based GUI client that connects to the controller and renders fish movements
- **Fish Programs**: Individual fish entities with different mobility patterns (RandomWayPoint, PathWay, etc.)

## Key Features
- **Centralized Architecture**: Single controller manages multiple display clients
- **Multi-threaded Server**: Handles multiple client connections using select() for efficient I/O multiplexing
- **Real-time Communication**: TCP-based protocol for fish position updates
- **Mobility Patterns**: Supports RandomWayPoint and other movement algorithms
- **Dynamic Topology**: Add/remove display views and fish during runtime
- **Configuration Management**: Load/save aquarium topologies from files

## Project Structure
- **serveur/**: Contains the C source code for the controller/server
- **client/**: Contains the Java source code for the display client
- **diag/**: Contains architecture diagrams and documentation
- **poisson/**: Contains graphical resources for fish rendering (PNG files)
- **config/**: Configuration files for server and client settings

## System Architecture
The aquarium uses a client-server architecture where:
- The **Controller** manages the global aquarium state (1000x1000 coordinate system)
- Multiple **Display Clients** connect to show different views of the aquarium
- Each display client has a specific viewport (e.g., N1: 0x0+500+500)
- Fish can move between different display views seamlessly

## Communication Protocol
The system uses a custom TCP protocol for client-server communication:

### Authentication
```
> hello in as N1
< greeting N1 0x0+500+500
```

### Fish Management
```
> addFish PoissonRouge at 90x40,10x4,RandomWayPoint
< OK

> getFishes
< list [PoissonRouge at 90x4,10x4,5] [PoissonClown at 20x80,12x6,5]

> startFish PoissonRouge
< OK
```

## Prerequisites
### Server
- GCC (C compiler)
- Make
- POSIX-compliant system (Linux/Unix)

### Client
- Java 11 or higher
- Maven (for dependency management)
- JavaFX (for GUI rendering)

## Installation and Usage

### Server Compilation and Execution
1. **Navigate to the server directory:**
   ```bash
   cd serveur
   ```

2. **Compile the server:**
   ```bash
   make
   ```

3. **Run the server:**
   ```bash
   ./serveur
   ```

4. **Load aquarium topology:**
   ```bash
   load aquarium1.txt
   ```

The server uses configuration files (aquarium1.txt, aquarium2.txt) to initialize the aquarium topology.

### Client Compilation and Execution
1. **Navigate to the client directory:**
   ```bash
   cd client
   ```

2. **Compile the client:**
   ```bash
   make compile
   ```

3. **Create executable package:**
   ```bash
   make package
   ```

4. **Run the client:**
   ```bash
   make run
   ```

## Configuration Files

### Display Configuration (affichage.cfg)
```
# Controller IP address
controller-address = 127.0.0.1

# Display client identifier
id = N1

# Controller TCP port
controller-port = 12345

# Ping timeout value (seconds)
display-timeout-value = 30

# Fish visual resources directory
resources = ./fishes
```

### Controller Configuration (controller.cfg)
```
# TCP listening port
controller-port = 12345

# Client timeout threshold (seconds)
display-timeout-value = 45

# Fish update interval (seconds)
fish-update-interval = 1
```

## Supported Commands

### Controller Commands
- `load aquarium1` - Load aquarium topology from file
- `show aquarium` - Display current topology
- `add view N5 400x400+400+200` - Add new display view
- `del view N5` - Remove display view
- `save aquarium2` - Save current topology to file

### Client Commands
- `status` - Show connection status and fish list
- `addFish PoissonNain at 61x52,4x3,RandomWayPoint` - Add new fish
- `delFish PoissonNain` - Remove fish
- `startFish PoissonNain` - Start fish movement

## Mobility Algorithms
- **RandomWayPoint**: Fish moves to random destinations with specified durations
- **PathWay**: Fish follows predefined paths (extensible for custom patterns)
- **HorizontalPathWay**: Fish moves horizontally across display boundaries

## Development Notes
- The project follows Agile development methodology
- Source code versioning managed through Thor forge
- LLM assistance (ChatGPT) was used for command parsing with appropriate referencing
- Multi-threading implemented using select() for optimal performance
- Fish visual assets are PNG files matched by name (ignoring underscore suffixes)

## Demo
A complete demonstration of the project is available at:
https://drive.google.com/file/d/1mFltOM9FLugce1VRzNLGor2_kT6WWNPD/view?usp=sharing

## Academic Context
This project was developed as part of the RE203 Networks course (March 2025) focusing on:
- Network programming in C and Java
- Client-server architecture design
- Real-time communication protocols
- Multi-threaded server implementation
- GUI development with JavaFX
