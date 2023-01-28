import numpy as np
from qiskit import QuantumRegister, ClassicalRegister
idx = QuantumRegister(0, 0)
intensity = QuantumRegister(0,0)
cr = ClassicalRegister(16, 'cr')
qc_image = QuantumCircuit(intensity, idx, cr)
num_qubits = 16
qc_image.draw()
