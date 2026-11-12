# Electronic Voting Machine (EVM) using Digital Logic Design

A 4-candidate electronic voting machine designed entirely with digital logic: gates, flip-flops, multiplexers and decoders. It uses no microcontroller and no programming.


## Features

- **Two modes:** Admin mode and Vote mode, chosen with a mode selector
- **Candidate selection:** a decoder-based candidate ID selector for 4 candidates
- **One vote per cycle:** an SR latch locks the machine after a vote until it is reset
- **Anti-repeat logic:** prevents a single button press from registering more than once
- **Vote counting:** a separate 3-bit counter per candidate, built from D flip-flops
- **Result display:** display multiplexers feed BCD-to-7-segment decoders and four 7-segment displays
- **Master reset:** clears the lock and the counters

## Components Used

| Type | Components |
|------|------------|
| Combinational | AND, OR, XOR, NOT gates, decoder, multiplexers, BCD to 7-segment decoder |
| Sequential | D flip-flops, SR latch (built from NOR gates) |
| Input / Output | Push buttons, clock, 7-segment displays, indicator LEDs |

## Block Overview

1. **Mode selector:** chooses between Vote mode and Admin (result viewing) mode.
2. **Candidate ID selector:** decodes the selected candidate (1 to 4) and lights the matching indicator.
3. **Lock latch (SR latch):** after a vote is cast, the machine locks until reset.
4. **Anti-repeat logic:** edge-detects the vote button so one press equals one vote.
5. **Vote counters:** each candidate has a 3-bit counter made of D flip-flops, so counts run from 0 to 7.
6. **Display multiplexers:** select which candidate's count is sent to the displays.
7. **BCD to 7-segment decoders:** convert the count to a digit on the display.

## How It Works

1. Set the mode selector to **Vote mode**.
2. Select a candidate with the candidate selector. The matching indicator lights up.
3. Press the **vote** button. The selected candidate's counter increments on the clock edge.
4. The SR latch locks, so no further votes are accepted.
5. Press **reset** to unlock the machine for the next voter.
6. Switch to **Admin mode** to view each candidate's total on the 7-segment displays.

## Tools

- Simulator: `LOGIC works'
- Project file: `circuit/` folder

## How to Run

1. Install the simulator listed above.
2. Open the project file from the `circuit/` folder.
3. Start the clock and the simulation.
4. Follow the steps in **How It Works** to cast votes and view results.



## Limitations

- Each counter is 3-bit, so the maximum is **7 votes per candidate**. Adding more flip-flops per counter extends this.
- Supports 4 candidates only.
- Votes are not stored permanently, so the counts clear when the simulation stops.

## Future Improvements

- Larger counters (4-bit or more) for more votes
- Voter ID or authentication logic
- Support for more candidates
- Total-votes counter and a tie indicator

## Author

**Ahmad Manzoor**

## License

This project was made for educational purposes.
