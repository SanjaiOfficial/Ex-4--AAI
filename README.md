<H3>ENTER YOUR NAME: SANJAI L</H3>
<H3>ENTER YOUR REGISTER NO.: 212223230184</H3>
<H3>EX. NO.4</H3>
<H3>DATE:06-08-2026</H3>
<H1 ALIGN =CENTER> Implementation of Hidden Markov Model</H1>

## Aim: 
Construct a Python code to find the sequence of hidden states by the known sequence of observances using Hidden Markov Model. Consider two hidden states Sunny and Rainy with observable states,happy and sad.

## Algorithm:

Step 1:Define the transition matrix, which specifies the probability of transitioning from  one hidden state to another.<br>
Step 2:Define the emission matrix, which specifies the probability of observing each possible observation given each hidden state.<br>
Step 3:Define the initial probabilities, which specify the probability of starting in each possible hidden state.<br>
Step 4:Define the observed sequence, which is the sequence of observations need to  be analyzed.<br>
Step 5:Initialize the alpha matrix with zeros, where each row represents a time step and each column represents a possible hidden state.<br>
Step 6:Calculate the first row of the alpha matrix by multiplying the initial  probabilities by the emission probabilities for the first observation.<br>
Step 7:Loop through the rest of the observed sequence and calculate the rest of the alpha matrix by multiplying the emission probabilities by the sum of the product of 
       the previous row of the alpha matrix and the corresponding row of the transition matrix.<br>
Step 8:Calculate the probability of the observed sequence by summing the last row of the alpha matrix.<br>
Step 9:Find the most likely sequence of hidden states by selecting the hidden state with the highest probability at each time step based on the alpha matrix.<br>

## Program:
Insert your Program here
```PY
import numpy as np

transition = np.array([
    [0.8, 0.2],   # Sunny -> Sunny, Rainy
    [0.4, 0.6]    # Rainy -> Sunny, Rainy
])

emission = np.array([
    [0.7, 0.3],   # Sunny -> Happy, Sad
    [0.4, 0.6]    # Rainy -> Happy, Sad
])

initial = np.array([0.6, 0.4])
observations = [0, 1, 0]  
alpha = np.zeros((len(observations), 2))
alpha[0] = initial * emission[:, observations[0]]

for t in range(1, len(observations)):
    for state in range(2):
        alpha[t, state] = emission[state, observations[t]] * np.sum(
            alpha[t-1] * transition[:, state]
        )


sequence_probability = np.sum(alpha[-1])

hidden_states = np.argmax(alpha, axis=1)

states = ["Sunny", "Rainy"]
result = [states[i] for i in hidden_states]

print("Alpha Matrix:")
print(alpha)

print("\nProbability of observed sequence:", sequence_probability)

print("\nMost likely hidden state sequence:")
print(result)

```

## Output:

<img width="1203" height="192" alt="Screenshot 2026-08-06 222330" src="https://github.com/user-attachments/assets/e298e2e9-1763-45d1-a7dd-f7239c591643" />

## Result:
Thus Hidden Markov Model is implemented using python.

