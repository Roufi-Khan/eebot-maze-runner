# EEbot Maze Runner

A three-woman group project for COE538 at Toronto Metropolitan University, using HCS12 assembly to control an EEbot robot through a marked maze.

The project combines optical sensor readings, motor control, bumper inputs, and a finite-state machine to follow a path and respond to turns and contact.

## Hardware and Tools

- HCS12 / MC9S12C32 microcontroller
- Five optical guider sensors
- Two drive motors
- Front and rear bumper switches
- LCD display
- CodeWarrior development environment
- HCS12 assembly language

## How It Works

The program repeatedly reads the optical sensors, updates the LCD, and executes the movement routine associated with the robot's current state.

Sensor readings are compared with calibrated reference values to guide movement. Motor direction and enable signals control forward motion, reversing, and turns.

The movement states include:

- Start
- Forward
- Stopped
- Left and right turns
- Reverse-turn recovery
- Left and right alignment corrections

The LCD displays the battery voltage and current operating state.

Navigation uses predefined rules and current sensor readings. This version does not store a maze map or calculate a shortest path.

## Testing and Results

The robot worked during our practice runs. During the graded demonstration, it veered off course at a later fork in the maze.

The root cause was not confirmed. Further investigation would focus on sensor readings, approach alignment, movement timing, and state transitions at that junction.

## Project Files

| File or folder | Purpose |
| --- | --- |
| `Sources/main.asm` | Main robot control program |
| `Sources/derivative.inc` | Includes the microcontroller-specific definitions |
| `FinalProject.mcp` | CodeWarrior project file |
| `Full_Chip_Simulation.ini` | Simulator configuration |
| `cmd/` | Debugger and simulator command files |
| `prm/` | Build configuration |
| `ASM_layout.hwl` | Debugger window layout |
| `Default.mem` | Memory configuration |

Generated build outputs and local workspace data are excluded.

## Opening the Project

Open `FinalProject.mcp` in a compatible CodeWarrior installation with HCS12 support.

The project references `mc9s12c32.inc`, which must be available through the development environment. Physical navigation requires the corresponding EEbot hardware and sensor calibration.

## Possible Improvements

- Replace blocking movement delays with timer-based transitions.
- Check bumper inputs consistently across movement states.
- Review turn-completion and state-dispatch logic.
- Record sensor readings and state transitions during testing.
- Repeat junction tests with different approach positions.

## Team and Acknowledgments

This project was completed collaboratively by a team of three students, including Roufi Shahrin Khan. It represents shared team work rather than an individual project.

The source includes supplied CodeWarrior framework code and supporting routines used in the course project. Existing comments and acknowledgments are retained.
