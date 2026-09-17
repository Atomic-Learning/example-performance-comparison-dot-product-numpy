In this page, we will compare the performance of four different methods of calculating the dot product of a sequence. In each case, we will create a sequences (either a list or a NumPy array), each containing the values 0-9999 and measure how long it takes to take the dot product of the sequence with itself. We will repeat the process 100 times in each case to get a more accurate measurement of the execution time.

# The Accumulator Pattern

The most basic method is to use the accumulator pattern to manually calculate the dot product by iterating through the sequence and summing the products of corresponding elements.

```py-cell
from time import time

# Don't worry if you're not familiar with this method or creating a list from a range
sequence = list(range(10000))

start_time = time.time()
dot_product = 0
for i in range(len(sequence)):
    dot_product += sequence[i] * sequence[i]
end_time = time.time()

execution_time = end_time - start_time
print("Execution time: ", execution_time, "seconds")
```

# Sum of a Generator Expression

This is a much more advanced method of calculating the dot product using a generator expression inside the `sum` function. Don't worry if you don't fully understand the code - the important thing to know is that this is one of the most efficient ways fo calculating the dot product of a number with itself using native Python.

```py-cell
from time import time

sequence = list(range(10000))

start_time = time.time()
dot_product = sum(x * x for x in sequence)
end_time = time.time()

execution_time = end_time - start_time
print("Execution time: ", execution_time, "seconds")
```

# Sum of a NumPy Multiplication

This method uses NumPy to perform element-wise multiplication of the sequence with itself and then sums the result.

```py-cell
import numpy as np
from time import time

sequence = np.arange(10000)

start_time = time.time()
dot_product = np.sum(sequence * sequence)
end_time = time.time()

execution_time = end_time - start_time
print("Execution time: ", execution_time, "seconds")
```

# NumPy Dot Function

This method uses the built-in `np.dot` function to calculate the dot product directly.
```py-cell
import numpy as np
from time import time

sequence = np.arange(10000)

start_time = time.time()
dot_product = np.dot(sequence, sequence)
end_time = time.time()

execution_time = end_time - start_time
print("Execution time: ", execution_time, "seconds")
```