import numpy as np
import qiskit
from qiskit import QuantumCircuit 
from qiskit import QuantumRegister, ClassicalRegister
idx = QuantumRegister(2, 'idx')
intensity = QuantumRegister(16,'intensity')
cr = ClassicalRegister(10, 'cr')
qc_image = QuantumCircuit(intensity, idx, cr)
num_qubits = 16
qc_image.draw()
for idx in range(it.size):
    qc_image.i(idx)  
qc_image.h(16)
qc_image.h(17)
qc_image.barrier()
qc_image.draw()
for idx in range(num_qubits):
    qc_image.i(idx)
qc_image.barrier()
qc_image.draw()
value01 = '01100100'
qc_image.x(qc_image.num_qubits-1)
for idx, px_value in enumerate(value01[::-1]):
    if(px_value=='1'):
        qc_image.ccx(num_qubits-1, num_qubits-2, idx)
qc_image.x(num_qubits-1)
qc_image.barrier()
qc_image.draw()
value10 = '11001000'
qc_image.x(num_qubits-2)
for idx, px_value in enumerate(value10[::-1]):
    if(px_value=='1'):
        qc_image.ccx(num_qubits-1, num_qubits-2, idx)
qc_image.x(num_qubits-2)
qc_image.barrier()
qc_image.draw()
value11 = '11111111'
for idx, px_value in enumerate(value11):
    if(px_value=='1'):
        qc_image.ccx(num_qubits-1,num_qubits-2, idx)
qc_image.barrier()
qc_image.measure(range(10),range(10))
