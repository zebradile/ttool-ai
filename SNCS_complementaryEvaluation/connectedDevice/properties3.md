Based on the given system specification, here are three properties to verify on the connected pumpkin system and the methods to proceed with their verification:

### Property 1: Activation of LEDs in Darkness
**Specification:** The connected pumpkin must light up its LEDs as soon as it is placed in the dark.

**Verification Method:**
- **Observer Block:** An observer block can be designed to monitor the light sensor input and the LED activation signal. 
- **Verification Steps:**
  1. Create an observer block to monitor the state of the light sensor (e.g., `lightSensorState`) and the LED activation signal (e.g., `LEDState`).
  2. Define the observer logic to check if `LEDState` becomes active (`ON`) when `lightSensorState` indicates darkness (`LOW` or `0`).
  3. Simulate the system with varying light sensor inputs and observe the LED state.
  4. Ensure the observer block validates that whenever the light sensor detects darkness, the LEDs are turned on.

### Property 2: Song Selection on Halloween Night
**Specification:** The connected pumpkin must sing the Ghostbusters theme on Halloween night regardless of any other conditions.

**Verification Method:**
- **CTL Property (Computation Tree Logic):** Use a temporal logic formula to ensure the system behaves as expected on Halloween night.
- **Verification Steps:**
  1. Define a CTL property to check the state of the system on Halloween night.
     - Example CTL property: `AG (isHalloweenNight -> AF (currentSong = "GhostbustersTheme"))`
  2. Use a model checker to verify that this CTL property holds true in all possible states and transitions of the system.
  3. Ensure the model includes the calendar date check to identify Halloween night and the logic that selects the Ghostbusters theme song.

### Property 3: WiFi Communication Integrity
**Specification:** The connected pumpkin must correctly report the currently playing song to the iPumpkin application in real time.

**Verification Method:**
- **Observer Block and CTL Property:** Use an observer block to monitor the song being played and a CTL property to ensure real-time communication.
- **Verification Steps:**
  1. Create an observer block to monitor the `currentSong` being played and the data sent over the WiFi interface (`wifiSongReport`).
  2. Define the observer logic to check that `wifiSongReport` matches `currentSong` at all times.
  3. Define a CTL property to verify real-time communication integrity.
     - Example CTL property: `AG (currentSong = wifiSongReport)`
  4. Simulate various scenarios where songs change, and ensure the observer block validates the real-time update of the song being reported over WiFi.
  5. Use a model checker to verify the CTL property holds true, ensuring the WiFi communication correctly reflects the current state of the system.

By using these verification methods (observer blocks for dynamic monitoring and CTL properties for temporal logic checking), you can ensure that the connected pumpkin system meets its specified requirements and behaves correctly in various scenarios.
