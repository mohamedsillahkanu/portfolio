# Step-by-step guide for running a basic simulation script to analyze climate and vector (mosquito) dynamics, aimed at understanding how environmental factors and vector behavior impact malaria transmission.


### Step 1: Open MobaXterm on your computer, select 'Start Local Terminal' or use the SSH option, and log in to Quest using your credentials."

![Login](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/Login.png)

- **Note: MobaXterm is typically used to work on remote servers (e.g., through SSH)**
    - **SSH (Secure Shell) is a network protocol that allows you to securely connect to a remote computer or server over a secured network. It is widely used by system administrators, developers, and IT professionals to manage remote systems, transfer files, and execute commands.**

### Step 2: Screen that appears after you successfully log in.

![Aftter_Login](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/After%20login.png)

### Step 3: Load the Python module in the terminal as it is already pre-installed.

```python
module load python/3.8.4
```
- Note: idmtools require python 3.7 or higher


### **Step 4: Create and Activate a Virtual Python Environment**

1. **Create the Virtual Environment**:
   Run the following command to create a virtual environment named `test`:
   ```python
   python -m venv test
   ```
2. **Activate the Virtual Environment**:
   Activate the virtual environment using the following command:
   ```python
   source /home/wko2809/test/bin/activate
- Note: **test** is the name of the virtual environment used in this example.
- **/home/wko2809/test/** is the file path where the virtual environment is located.

![virtual_exp](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/virtula%20environment.png)

### Step 5: Install emodpy-malaria

```python
pip install emodpy-malaria --ignore-installed --index-url=https://packages.idmod.org/api/pypi/pypi-production/simple
```
![emodpy_malaria](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/emodpy-malaria.png)
![emodpy2](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/emodpy2.png)


### Step 6: Install idmtools_platform_slurm

```python
 pip install idmtools_platform_slurm --ignore-installed --index-url=https://packages.idmod.org/api/pypi/pypi-production/simple
```

![idmtools1](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/idmtools1.png)
![idmtools2](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/idmtools2.png)

### Step 7: Update the .bashrc file to automatically activate the virtual environment by adding the following command:

```python
alias load_emodpy='source /home/wko2809/test/bin/activate'
```

![bashrc](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/bashrc.png)


### **Step 8: Create a Directory in the Projects Folder**
Run the following commands to navigate to the `/projects/b1139/` folder and create a directory named `FE_test`:

```python
cd /projects/b1139/
mkdir FE_test
```

![mkdir](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/mkdir2.png)
### **Step 9: Clone the `FE-2023-examples` Repository into the `FE_test` Folder**

Clone the repository:
```python
git clone https://github.com/mohamedsillahkanu/FE-2023-examples.git
```
**Or you clone this**                           
```python
git clone https://github.com/numalariamodeling/FE-2023-examples.git
```
**Note:** Ensure you are in the `FE_test` folder before cloning the repository.

![gitclone](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/gitclone.png)

### **Step 10: Run a simple simulation using the `run_example.py` file**

To execute the simulation, run the following command:
```python
cd FE-2023-examples/
```
```python
python3 run_example.py
```
![gitclone](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/run_example.png)


### **Step 11: Step-by-Step Explanation of the Output**

![sim_output](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/sim_output.png)

#### **11.1. Initialization of SlurmPlatform**
```plaintext
Initializing SlurmPlatform with:
{
   "mode": "local",
   "job_directory": "/projects/b1139/FE_wko2809/FE-2023-examples/experiments",
   "time": "2:00:00",
   "max_running_jobs": 10,
   "modules": [
      "singularity"
   ],
   "partition": "b1139testnode",
   "account": "b1139"
}
```
- **What Happened?**
  - The **SlurmPlatform** is initialized to manage the simulations.
  - Configuration:
    - **Mode**: `local` – The simulations will run on one specific compute node within the HPC system.
    - **Job Directory**: `/projects/b1139/FE_wko2809/FE-2023-examples/experiments` – The output files will be stored here.
    - **Time**: `2:00:00` – The maximum runtime for jobs is 2 hours.
    - **Max Running Jobs**: `10` – Allows up to 10 jobs to run at the same time.
    - **Modules**: Includes `singularity`, the container runtime.
    - **Partition**: `b1139testnode`, a specific Slurm partition (node group).
    - **Account**: `b1139`, your account for Slurm resource allocation.

---

#### **11.2. Creation of EMODTask**
```plaintext
Creating EMODTask (from files)...
```
- **What Happened?**
  - An **EMODTask** is being created. This task includes:
    - Simulation configuration.
    - Input files
    - Experiment parameters.
---

#### **11.3. Generating the Demographics File**
```plaintext
Generating demographics file demographics.json.
```
- **What Happened?**
  - A demographics file (`demographics.json`) is created. This file contains demographic data needed for the simulation.

---

#### **11.4. Discovering Experiment Assets**
```plaintext
Discovering experiment assets from tasks: 100%|████████████████████████████████████████████████████████████| 1/1 [00:00<00:00, 3315.66simulation/s]
```
- **What Happened?**
  - The system scans and links required input files for the experiment.
  - In this case, 1 task was successfully discovered and validated.

---

#### **11.5. Commissioning Simulations**
```plaintext
Commissioning Simulations: 100%|█████████████████████████████████████████████████████████████████████████████| 1/1 [00:00<00:00,  5.76simulation/s]
```
- **What Happened?**
  - The simulation is sent to the Slurm scheduler for execution.
  - 1 simulation was commissioned successfully.

---

#### **11.6. Job Directory, Suite, and Experiment Details**
```plaintext
job_directory: /projects/b1139/FE_wko2809/FE-2023-examples/experiments
suite: db030038-a91f-4618-851f-068af94be557
experiment: 784f07a9-de53-43e7-a175-a99ccd18dec0
```
- **What Happened?**
  - **Job Directory**: Location where outputs, logs, and results are stored.
  - **Suite ID**: `db030038-a91f-4618-851f-068af94be557` – Identifies the collection of related experiments.
  - **Experiment ID**: `784f07a9-de53-43e7-a175-a99ccd18dec0` – Identifies the specific experiment.

---

#### **11.7. Experiment Directory**
```plaintext
Experiment Directory:
/projects/b1139/FE_wko2809/FE-2023-examples/experiments/Suite_db030038-a91f-4618-851f-068af94be557/wko2809_FE_example_basic_784f07a9-de53-43e7-a175-a99ccd18dec0
```
- **What Happened?**
  - The full path to the directory containing outputs for this specific experiment.

---

#### **11.8. Slurm Job ID**
```plaintext
Slurm Job Ids (1):
   2263860
```
- **What Happened?**
  - The job is submitted to Slurm and assigned a Job ID (`2263860`).
  - This ID can be used to monitor the job’s status.

---

#### **11.9. Command to Check Job Status**
```plaintext
You may try the following command to check simulations running status:
  idmtools slurm /projects/b1139/FE_wko2809/FE-2023-examples/experiments status --exp-id 784f07a9-de53-43e7-a175-a99ccd18dec0
```
- **What Happened?**
  - You are given a command to monitor the status of the experiment using IDMTools.

---

#### **11.10. Simulation Progress**
```plaintext
Waiting on Experiment wko2809_FE_example_basic to Finish running: 100%|██████████████████████████████████████| 1/1 [01:00<00:00, 60.51s/simulation]
```
- **What Happened?**
  - The simulation is running, and the progress bar shows completion.
  - The simulation took approximately 1 minute (`60.51 seconds`) to run.

---

#### **11.11. Experiment Success**
```plaintext
Experiment 784f07a9-de53-43e7-a175-a99ccd18dec0 succeeded.
```
- **What Happened?**
  - The simulation completed successfully without errors.

### **Step 12: Update the Experiment ID in `analyzer_W1.py`**

#### **12.1 Copy the Experiment ID**:
   - Locate the **Experiment ID** from the output of the simulation. Example:
     ```plaintext
     experiment: 784f07a9-de53-43e7-a175-a99ccd18dec0
     ```

**Output file of the experiment (InsetChat.json)**

![idmtools2](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/InsetChat.png)



#### **12.2 Open `analyzer_W1.py`**:
   - Use a text editor to open the script:
   

#### **12.3 Replace the Experiment ID**:
   - Find the placeholder or old Experiment ID in the script.
   - Replace it with the new Experiment ID you copied.

#### **12.4 Save and Exit**:
   - Save your changes and exit the editor.

![analyzerW1](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/analyzerW1.png)

### Step 13: Once the Experiment ID is updated, run the script:

```python
python3 run analyzer_W1.py
```

### **Step 14: Explanation of the Analysis Process**

![analyzeroutput](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/analyzeroutput.png)

#### **14.1. Initializing the SlurmPlatform**
```plaintext
Initializing SlurmPlatform with:
{
   "mode": "local",
   "job_directory": "/projects/b1139/FE_wko2809/FE-2023-examples/experiments"
}
```
- **What Happened?**
  - The `SlurmPlatform` is initialized in **`mode: local`**.
  - This means the analysis is being run on a single machine (e.g., the same node or local machine) using the specified directory `/projects/b1139/FE_wko2809/FE-2023-examples/experiments` to access experiment data.

---

#### **14.2. Analyze Manager**
```plaintext
Analyze Manager
 | 1 item(s) selected for analysis
```
- **What Happened?**
  - The `Analyze Manager` has identified **1 item** (InsetChat.json) for analysis.
  - This is the output file (InsetChat.json) generated from the earlier simulation.
---

#### **14.3. Analysis Configuration**
```plaintext
 | partial_analyze_ok is True, max_items is None, and 0 item(s) are being ignored
```
- **What Happened?**
  - **`partial_analyze_ok: True`**:
    - Allows the analysis to proceed even if all expected items aren’t present.
    - This is useful for debugging or working with incomplete datasets.
  - **`max_items: None`**:
    - There’s no limit on the number of items that can be analyzed.
  - **`0 item(s) ignored`**:
    - All items selected for analysis are valid and included.

---

#### **14.4. Analyzer(s) Identified**
```plaintext
 | Analyzer(s):
 |  - SimpleInsetChartAnalyzer File parsing: on / Use cache: off
```
- **What Happened?**
  - The `Analyze Manager` uses a specific tool called **`SimpleInsetChartAnalyzer`**.
  - **`File parsing: on`**:
    - The analyzer parses data from the relevant files to extract useful insights.
  - **`Use cache: off`**:
    - It doesn’t rely on cached results, ensuring fresh data processing.

---

#### **14.5. Pool of Processes**
```plaintext
 | Pool of 1 analyzing process(es)
```
- **What Happened?**
  - The analysis uses **1 process** to perform the task.
  - This indicates the analysis is single-threaded, which is sufficient since only one item is being processed.

---

#### **14.6. File Parsing Progress**
```plaintext
100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1/1 [00:00<00:00,  3.10it/s]
```
- **What Happened?**
  - The file parsing step completes successfully.
  - Progress Bar:
    - **`1/1`**: 1 file has been parsed (out of 1 total).
    - **`3.10 it/s`**: The parser processed the file at a speed of 3.10 items per second.

---

#### **14.7. Running Analyzer Reduces**
```plaintext
Running Analyzer Reduces: 100%|██████████████████████████████████████████████████████████████████████████████████████| 1/1 [00:00<00:00,  7.10it/s]
```
- **What Happened?**
  - The reduction step of the analysis runs successfully.
  - This step processes the parsed data further.
  - **Speed**:
    - **`7.10 it/s`**: The reduction phase processed the data at a speed of 7.10 items per second.

---

#### **14.8. Analysis Completion**
```plaintext
 | Analysis complete. Took 0 seconds (~ 0.477 per item)
```
- **What Happened?**
  - The analysis is finished.
  - **Time Taken**:
    - The total time was **0 seconds**, as the task was extremely lightweight.
    - On average, it took **0.477 seconds per item** to process.

### Step 15: Navigate to the Directory to View All Files
To view all the output files generated by the simulation and analysis, navigate to the following directory:

```python
cd /projects/b1139/FE_wko2809/FE-2023-examples/experiments/my_outputs/example_basic/
```

### Step 16: View the Plots to Assess Simulation Performance
#### Goal: The goal of analyzing climate and vector (mosquito) dynamics is to understand how environmental factors and vector behaviors influence the transmission of vector-borne diseases, such as malaria.

**All Ages InsetChart Climate Vector**

![output1](https://raw.githubusercontent.com/mohamedsillahkanu/FE-2023-examples/main/All_Age_InsetChart_climate_vectors.png)

#### **16.1. Adult Vectors**
- **Y-axis**: Number of adult vectors (mosquitoes).
- **X-axis**: Time (days or simulation ticks).
- **Observation**: 
  - The values seem constant over time, indicating no significant change in the adult vector population.

#### **16.2. Air Temperature**
- **Y-axis**: Air temperature (likely in °C).
- **X-axis**: Time.
- **Observation**:
  - The temperature remains consistent throughout the simulation, suggesting no variation in the climate model.

#### **16.3. Daily Bites per Human**
- **Y-axis**: Number of bites per human per day.
- **X-axis**: Time.
- **Observation**:
  - This is constant, indicating a fixed biting rate of vectors on humans.

#### **16.4. Daily EIR (Entomological Inoculation Rate)**
- **Y-axis**: Daily EIR, measuring the rate at which humans are exposed to infectious bites.
- **X-axis**: Time.
- **Observation**:
  - The EIR remains constant, implying stable transmission risk throughout the simulation.

#### **16.5. Human Infectious Reservoir**
- **Y-axis**: Proportion of infectious humans contributing to transmission.
- **X-axis**: Time.
- **Observation**:
  - A peak is observed early in the simulation, suggesting an initial surge in human infectiousness, which tapers off over time.

#### **16.6. Infectious Vectors**
- **Y-axis**: Number of infectious vectors (mosquitoes).
- **X-axis**: Time.
- **Observation**:
  - This remains constant, showing a stable population of infectious vectors.

#### **16.7. Rainfall**
- **Y-axis**: Rainfall amount (likely in mm).
- **X-axis**: Time.
- **Observation**:
  - Rainfall remains steady, indicating no seasonal or climate-driven changes.

#### **16.8. Relative Humidity**
- **Y-axis**: Relative humidity (fraction or percentage).
- **X-axis**: Time.
- **Observation**:
  - Relative humidity is constant, suggesting no environmental variability in this parameter.

---

### 16.9 **General Observations**
1. **Consistency Across Parameters**:
   - Most parameters (temperature, rainfall, relative humidity, biting rate, and vector population) remain constant over time, implying the model is simulating a stable environment.

2. **Dynamic Behavior**:
   - The only dynamic parameter is **Human Infectious Reservoir**, which shows an initial peak and then stabilizes. This might represent an outbreak or a short-term increase in infections that decline over time.




