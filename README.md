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
