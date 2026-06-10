# Qiskit with Machine Learning Qubit Noise Classifier
This project is a basic project that I create to learn Qiskit with quantum qubit characteristics, I want to learn how noises are affect to qubits however this is not a big project if you think this is help to understand I really thanks so much.
The goal is to see if a classical ML model can understand and predict how bad the noise is just by looking at the output data from a quantum circuit.

## The Idea
I create a 5-qubit **GHZ State** (a type of quantum entangled state) and simulate it using **Qiskit** and **AerSimulator** from IBM tool. 

In an ideal world, the output should only be 00000 or 11111. But because of quantum noise, we get some useless states in between. By tweaking the noise scale, we generated 5 different levels of noise:
* **Very Low** (1.0x - normal backend noise)
* **Low** (1.1x noise)
* **Middle** (1.2x noise)
* **High** (1.3x noise)
* **Very High** (1.4x noise)

## Feature Engineering (The Secret Sauce)
Instead of just giving raw probability data to the ML model, we calculated some clever quantum features that make the model way smarter:
1. **Total Variation Distance (TVD):** How far away our noisy output is from the ideal world.
2. **Quantum Entropy:** Measuring the randomness/chaos of the state.
3. **Fidelity Estimate:** How close we are to the perfect GHZ state.
4. **Noise Leakage:** The sum of all the useless states that shouldn't exist.
5. **Parity Contrast:** Checking the symmetry between even and odd bitstrings.

## Results
* **Quantum Setup:** 5 Qubits, 4,096 Shots (to get clean statistical data).
* **ML Model:** Random Forest Classifier.
* **Accuracy:** **~85%** (**acceptable in my opinion**)

This is an awesome result because I think classifying 5 classes that are very close to each other is a tough job.

## Project Structure
* `1.Qiskit with ML Qubit Noise Classifier.ipynb`: The main Jupyter Notebook containing all the code from simulation, data collection, model training, to plotting the learning curve and confusion matrix.

## 🛠️ How to Run
1. Basic install requirements:
   ```bash
   pip install qiskit qiskit-aer numpy pandas scikit-learn matplotlib seaborn
