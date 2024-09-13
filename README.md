Event Log Generation and Process Mining with PM4Py
This project demonstrates how to generate a synthetic event log and perform process mining using the PM4Py library. The generated event log simulates a process for purchasing items either online or at a store. The event log is then analyzed using the Alpha Miner algorithm and Directly-Follows Graph (DFG) discovery techniques.

Prerequisites
To run the code, ensure you have the following installed:

Python 3.6 or higher
PM4Py library
Pandas
NumPy
You can install the necessary Python packages using the following command:

bash
Copy code
pip install pm4py pandas numpy
Generating an Event Log
The script provided generates a synthetic event log that simulates a process for purchasing items online or at a store. The process includes various activities such as checking balance, making payment, preparing goods, and more. Each activity is associated with logical durations and dependencies.

Steps to Generate the Event Log:
Define Activities and Dependencies: The script defines a list of activities with their dependencies and possible next steps.
Generate Logs for Each Case: Logs are generated for each case, simulating the progression of activities over time.
Add Resources and Location: Random resources (e.g., store or website names) and locations (e.g., cities) are added to each case.
Save the Event Log: The generated event log is saved as a CSV file named purchase_logs_loreal.csv.
Usage:
python
Copy code
# Generate dataset with 500 cases
num_cases = 500
dataset = generate_dataset(num_cases)

# Save the dataset to a CSV file
df.to_csv('purchase_logs_loreal.csv', index=False)
Process Mining with PM4Py
Once the event log is generated, you can perform process mining using PM4Py.

Steps for Process Mining:
Convert Event Log to XES: The generated event log in CSV format can be converted to XES format using ProM or any other tool.
Import the Event Log: Import the XES file using PM4Py.
Apply Alpha Miner: Use the Alpha Miner algorithm to discover a Petri net model of the process.
Visualize the Petri Net: Visualize the discovered Petri net.
Discovering and Visualizing DFG:
Additionally, the script allows you to discover and visualize the Directly-Follows Graph (DFG) from the event log.

Usage:
python
Copy code
# Import the log
log_path = 'the Process.xes'  # The XES file of the generated dataset
log = xes_importer.apply(log_path)

# Apply Alpha Miner
net, initial_marking, final_marking = alpha_miner.apply(log)

# Visualize the Petri net
gviz = pn_visualizer.apply(net, initial_marking, final_marking)
pn_visualizer.view(gviz)

# Discover and visualize the DFG
dfg = dfg_discovery.apply(log)
gviz = dfg_visualizer.apply(dfg, parameters={"format": "png"})
dfg_visualizer.view(gviz)
License
This project is licensed under the MIT License - see the LICENSE file for details.
