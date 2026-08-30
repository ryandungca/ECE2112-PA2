# ECE2112: Programming Assignment 2
**Ryan Joseph C. Dungca, 2ECE-D**

This repository contains code for Programming Assignment 2 of the course ECE2112, covering three problems related to _Module 2 - Numpy_. The creation of this code demonstrates the ability to:
- create and reshape NumPy arrays using appropriate NumPy functions;
- perform vectorized numerical operations on an ndarray;
- compute array statistics and use Boolean conditions to select elements; and
- save computed NumPy arrays as .npy files.

To view the code itself, access the [related Python notebook file](ECE2112-PA2.ipynb). Additionally included are the [three](X_normalized.npy) [.npy](div_by_4.npy) [files](above_mean.npy) required by all three problems. 

# A. Reproducible Normalization Problem
>_Objective_: Create a reproducible random 5 × 5 integer ndarray named `X`. Use the following two statements before performing any calculation: `np.random.seed(2112)` `X = np.random.randint(10, 101, size=(5, 5))` Normalize the complete array using Z = (X − ¯x)/σ , where ¯x is the mean of all 25 elements and σ is their population standard deviation as returned by NumPy’s default `std()` call. Store the normalized array in `X_normalized`.

The first two lines for the problem solution are: 
- `np.random.seed(2112)`, which sets the "seed" to 2112, ensuring that any later randomizations are reproducible with that seed, and
- `X = np.random.randint(10, 101, size=(5, 5))`, which constructs the random 5 × 5 integer array `X`, with random values from 10 to 100, and the prescribed size of 5 rows and columns. Note that the function's upper limit for random integers does not include the input number; thus, the upper limit for the function is listed as `101` to include the actual limit of 100.

After this, the array `X` must be normalized using the provided formula, with this new array being saved to `X_normalized`. As two other values, specifically the mean and population standard deviation, are required to use the formula, they are provided by the built-in NumPy functions `np.mean()` and `np.std()`, respectively. Using these values directly in the formula, the new array is constructed by `X_normalized = (X - np,mean(X))/np.std(X)`, where the functions use the array `X` as an argument to return its mean and population standard deviation.

All the required tests for the problem are then outputted by `print()`. Finally, the array `X_normalized` must be saved to a .npy file of a corresponding name. This is performed by `npy.save("X_normalzed.npy", X_normalized)`, which specifies the file name as the first argument, and the array to be saved as the second argument.

The constructed solution, omitting `import numpy as np` and tests, is:
```
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
X_normalized = (X-np.mean(X))/np.std(X)
np.save("X_normalized.npy", X_normalized)
```

# B. Cubes Divisible by 4 Problem
>_Objective_: Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named `C`. Thus, `C` begins with 1³ and ends with 100³. Use a Boolean condition on `C` to obtain every cubed value divisible by 4. Store the selected values in `div_by_4`. Preserve NumPy’s normal row-major selection order.

To construct an array with the first 100 positive integers, the line `C = np.arange(1, 101)` is used, which constructs an array with elements from 1 to 101, but not including 101; effectively, 1 to 100. Additionally, a third argument can be given for the function to specify the step between elements, which defaults to 1 if not specified; in this case, since the problems specifies using the first 100 positive integers, this step argument is left to default.

Each element of the array is then cubed. For this solution, the line `C = np.power(C, 3)` is used, where the built-in function `np.power()` exponentiates the array provided as the first argument by the value provided in the second argument, here being 3 to cube the array. More simply, the basic Python exponentiation function can be used by `C = C**3`. The array is then reshaped by stacking the built-in method `.reshape()`, which re-shapes the array into a 10 × 10 array.

A new array `div_by_4` must then be constructed, containing only every cubed value of `C` divisible by 4. With the hint to use boolean conditions, the array is constructed by `div_by_4 = C[C%4==0]`, using boolean indexing `C[condition]`, where the condition that the elements of `C` to be used must have no remainder when divided by 4 is imposed by the modulo and equality operators.

All the required tests for the problem are then outputted by `print()`. The tests for `C.shape` and `div_by_4.size` are included, to indicate the correct reshaping of `C` into a 10 × 10 array, and the correct sorting and amount of elements in `div_by_4`, respectively. Finally, using the same method as previously, `npy.save("div_by_4.npy", div_by_4)` saves this array to a correspondingly named .npy file. 

The constructed solution, omitting `import numpy as np` and tests, is:
```
C = np.arange(1,101)
C = np.power(C, 3).reshape(10, 10)
div_by_4 = C[C%4==0]
np.save("div_by_4.npy", div_by_4)
```

# C. Above-Mean Squares Problem
>_Objective_: Create a 6 × 6 ndarray named `S` containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of `S` and store it in `S_mean`. Then use Boolean filtering to select only the elements strictly greater than `S_mean`. Store these values in `above_mean`.

The array `S` is first constructed by `S = np.arange(1, 37).reshape(6, 6)`, which constructs the array of numbers from 1 to 37, but not including 37, with a step value defaulting to 1. The `reshape()` method is then stacked to reshape the constructed array into a 6 × 6 array. The elements of the array are then squared by `S = np.power(S, 2)`, or alternatively by `S = S**2`. The mean of all elements is then computed and stored into the variable `S_mean` by `S_mean = np.mean(S)`.

The array `above_mean` is then constructed to include elements of `S` that are above the previously-generated mean `S_mean`, by `above_mean = S[S>S_mean]`. This uses boolean indexing on `S`, with the provided condition that the elements must be greater than `S_mean`.

All required tests for the problem are outputted by `print()`. Included is the test for `above_mean.size`, indicating the correct amount of elements above the generated `S_mean`. The same method for saving an array to a file is then used by `np.save("above_mean.npy", above_mean)`.

The constructed solution, omitting `import numpy as np` and tests, is:
```
S = np.arange(1, 37).reshape(6, 6)
S = np.power(S, 2)
S_mean = np.mean(S)
np.save("above_mean.npy", above_mean)
```

## History
- 2026, August 27: File created. Uploaded and linked notebook and related NumPy array files.
- 2026, August 30: Added explanations for each problem solution; revised notebook uploaded.
