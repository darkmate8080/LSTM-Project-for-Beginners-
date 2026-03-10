# LSTM-Project-for-Beginners-
# What is LSTM - Long Short Term Memory?
Long Short-Term Memory (LSTM) is an enhanced version of the <a href="https://www.geeksforgeeks.org/machine-learning/introduction-to-recurrent-neural-network/">Recurrent Neural Network (RNN)</a>.
designed by Hochreiter and Schmidhuber. LSTMs can capture long-term dependencies in sequential data making them ideal for tasks like language translation, speech recognition and time series forecasting. Unlike traditional RNNs which use a single hidden state passed through time LSTMs introduce a memory cell that holds information over extended periods addressing the challenge of learning long-term dependencies.
<div style="display: flex; flex-direction: row; gap: 10px; align: center;">
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20251215093010988409/introduction_to_lstms.webp" width="332" height="285" />
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20250528172141936296/architecture_of_lstms.webp" width="332" height="285" />
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20250528172142155011/applications_of_lstm_.webp" width="332" height="285" />
</div>

## Problem with Long-Term Dependencies in RNN

Recurrent Neural Networks (RNNs) are designed to handle sequential data by maintaining a hidden state that captures information from previous time steps. However they often face challenges in learning long-term dependencies where information from distant time steps becomes crucial for making accurate predictions for current state. This problem is known as the vanishing gradient or exploding gradient problem.

* **Vanishing Gradient:** *When training a model over time, the gradients which help the model learn can shrink as they pass through many steps. This makes it hard for the model to learn long-term patterns since earlier information becomes almost irrelevant.*
* **Exploding Gradient:** Sometimes gradients can grow too large causing instability. This makes it difficult for the model to learn properly as the updates to the model become erratic and unpredictable.
  
Both of these issues make it challenging for standard RNNs to effectively capture long-term dependencies in sequential data.

## LSTM Architecture
LSTM architectures involves the memory cell which is controlled by three gates:
1. **Input gate:** Controls what information is added to the memory cell.
2. **Forget gate:** Determines what information is removed from the memory cell.
3. **Output gate:** Controls what information is output from the memory cell.

This allows LSTM networks to selectively retain or discard information as it flows through the network which allows them to learn long-term dependencies. The network has a hidden state which is like its short-term memory. This memory is updated using the current input, the previous hidden state and the current state of the memory cell.

## Working of LSTM
LSTM architecture has a chain structure that contains four neural networks and different memory blocks called cells.
![gate_of_lstm](https://github.com/user-attachments/assets/7a2820cf-42dc-4422-80ac-a521abe31f32)

<p align="center"><sup>LSTM Model </sup></p>
1. Forget Gate
The information that is no longer useful in the cell state is removed with the forget gate. Two inputs x<sub>t</sub> (input at the particular time) and h<sub>t-1</sub> (previous cell output) are fed to the gate and multiplied with weight matrices followed by the addition of bias. The resultant is passed through sigmoid activation function which gives output in range of [0,1]. If for a particular cell state the output is 0 or near to 0, the piece of information is forgotten and for output of 1 or near to 1, the information is retained for future use. 

The equation for the forget gate is:

  <img width="1105" height="71" alt="image" src="https://github.com/user-attachments/assets/822729ab-4023-414d-8664-b282753e7727" />

Where:
* **W**<sub>t</sub> represents the weight matrix associated with the forget gate.
* [**h**<sub>t-1</sub>,**X**<sub>t</sub>] denotes the concatenation of the current input and the previous hidden state.
* **b**<sub>t</sub> is the bias with the forget gate.
* σ is the sigmoid activation function.
![forget_gate](https://github.com/user-attachments/assets/e9adfdc1-e2fc-47cf-8974-67fec6d35f20)
<p align="center">Forget Gate</p>

## 2. Input gate
The addition of useful information to the cell state is done by the input gate. First the information is regulated using the sigmoid function and filter the values to be remembered similar to the forget gate using inputs h<sub>t-1</sub> and X<sub>t</sub>. Then, a vector is created using tanh function that gives an output from -1 to +1 which contains all the possible values from h<sub>t-1</sub> and X<sub>t</sub>. At last the values of the vector and the regulated values are multiplied to obtain the useful information. The equation for the input gate is:

<img width="1105" height="131" alt="image" src="https://github.com/user-attachments/assets/5d491551-c54b-4443-8272-0fd35b7967e3" />
We multiply the previous state by f<sub>t</sub> effectively filtering out the information we had decided to ignore earlier. Then we add  
i<sub>t</sub> ⊙ C<sub>t</sub> which represents the new candidate values scaled by how much we decided to update each state value.

<img width="1101" height="82" alt="image" src="https://github.com/user-attachments/assets/23abe873-fd53-4ed3-b6d2-74a196c5d02a" />

where
* ⊙ denotes element-wise multiplication*
* tanh is activation function*

![input_gate](https://github.com/user-attachments/assets/a8b7b91c-4050-457d-86d1-2a545feb7e9a)

## 3. Output gate

The output gate is responsible for deciding what part of the current cell state should be sent as the hidden state (output) for this time step.First, the gate uses a sigmoid function to determine which information from the current cell state will be output. This is done using the previous hidden state h<sub>t-1</sub> and the current input x<sub>t</sub>:
<img width="1108" height="85" alt="image" src="https://github.com/user-attachments/assets/2d5ae26e-82c3-4c16-8d31-b839ed9758a1" />

Next, the current cell state C<sub>t</sub> s passed through a tanh activation to scale its values between −1 −1 and +1 +1. Finally, this transformed cell state is multiplied element-wise with O<sub>t</sub> to produce the hidden state h<sub>t</sub>:

<img width="1110" height="82" alt="image" src="https://github.com/user-attachments/assets/7e97d8ab-2d23-42a2-a0c4-1318cd49e990" />

Here:
* O<sub>t</sub> is the output gate activation.*
* C<sub>t</sub> is the current cell state.
* ⊙ represents element-wise multiplication.
* σ is the sigmoid activation function.

This hidden state h<sub>t</sub> is then passed to the next time step and can also be used for generating the output of the network.

![output_gate](https://github.com/user-attachments/assets/f22cf399-4813-4f9f-8e3a-7457d73687bb)
<p><sup>Output Gate</sup></p>





