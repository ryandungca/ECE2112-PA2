# ECE2112: Programming Assignment 2
**Ryan Joseph C. Dungca, 2ECE-D**

This repository contains code for Programming Assignment 2 of the course ECE2112, covering three problems related to _Module 2 - Numpy_. The creation of this code demonstrates the ability to:
- Create and reshape NumPy arrays using appropriate NumPy functions;
- Perform vectorized numerical operations on an ndarray;
- Compute array statistics and use Boolean conditions to select elements; and
- Save computed NumPy arrays as .npy files.

To view the code itself, access the related Python notebook file, which is currently yet to be uploaded.

# A. Reproducible Normalization Problem
>_Objective_: Create a reproducible random 5 × 5 integer ndarray named `X`. Use the following two statements before performing any calculation: `np.random.seed(2112)` `X = np.random.randint(10, 101, size=(5, 5))` Normalize the complete array using Z = (X − ¯x)/σ , where ¯x is the mean of all 25 elements and σ is their population standard deviation as returned by NumPy’s default `std()` call. Store the normalized array in `X_normalized`.

# B. Cubes Divisible by 4 Problem
>_Objective_: Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named `C`. Thus, `C` begins with 1³ and ends with 100³. Use a Boolean condition on `C` to obtain every cubed value divisible by 4. Store the selected values in `div_by_4`. Preserve NumPy’s normal row-major selection order.

# C. Above-Mean Squares Problem
>_Objective_: Create a 6 × 6 ndarray named `S` containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of `S` and store it in `S_mean`. Then use Boolean filtering to select only the elements strictly greater than `S_mean`. Store these values in `above_mean`.

## History
- 2026, August 27: File created.
