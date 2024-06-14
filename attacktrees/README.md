## Using Our Attack Tree Generator

### Step 1: Install TTool
First, you need to install TTool. Follow the instructions provided [here](https://ttool.telecom-paris.fr/installation.html).

### Step 2: Install CAPEC tracer
Once TTool is installed, you can install the CAPEC tracer. Execute this command in your terminal from the main TTool directory:

```bash
python3 -m pip install -r capectracer/requirements_capec_tracer.txt
```

### Step 3: Create a New Model
1. Open TTool.
2. Click on `File > New Model`.
3. In the main window, right-click and select `New Attack Tree`.
4. Right-click again and select `New Attack Tree Diagram`.

### Step 4: Use the LLM-based Attack Tree Generator
1. Click on the `AI` button located in the upper right corner.
2. The AI window will be displayed.

   **Optional:** 
   - Select `CAPEC tracer`.
   - Copy and paste the desired specification in the `Question` area of the AI window.
   - Click on `Start`.

3. Select `Attack Tree Generator`, then choose `Pipeline 3`.
4. Paste your system specification in the `Question` area. If you have used the CAPEC tracer, also paste the desired list of CAPECs (for instance, the ten first ones).
5. Click on `Start`.

### Step 5: Apply the AI Response
1. Once the AI has provided an answer, click on `Apply Response`.
2. The attack tree will now be drawn in the TTool main window.


## Structure of the Repository

In the `./models` directory, you will find the attack trees generated for each of the three case studies. These attack trees are created both manually and using our generation tool. Each case study directory contains the following:

- The system specification
- Three TTool models:
  1. **Manual Attack Trees**: Attack trees created by hand within a 1.30-hour time frame.
  2. **Generated Attack Trees (without CAPEC tracer option)**: Attack trees generated without the CAPEC tracer option.
  3. **Generated Attack Trees (with CAPEC tracer option)**: Attack trees generated with the CAPEC tracer option.

Additionally, each case study directory includes a CSV file containing detailed gradings and metrics.

