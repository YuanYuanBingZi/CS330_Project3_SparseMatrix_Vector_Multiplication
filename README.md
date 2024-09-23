# CS330_Project3_SparseMatrix_Vector_Multiplication
## Project Overview
This project implements a sparse matrix-vector multiplication (SpMV) in C using Compressed Sparse Row (CSR) format. The program reads a sparse matrix in the Matrix Market format and converts it from Coordinate (COO) format to CSR. It then performs the matrix-vector multiplication and outputs the result, which can be compared with a provided solution.

## Key Features
- **Efficient CSR Conversion**: The function `convert_coo_to_csr` converts a matrix from COO to CSR format in O(N) time, ensuring the implementation can handle large matrices efficiently.
- **Sparse Matrix-Vector Multiplication**: The core functionality of the project is the `spmv` function, which performs matrix-vector multiplication using the CSR format.
- **Floating-Point Precision Handling**: Special attention is given to handling floating-point precision errors, ensuring the results are consistent with the provided solution, within a reasonable tolerance.

## File Descriptions
- `A.mtx`: The input sparse matrix in Matrix Market format.
- `x.mtx`: The input vector to be multiplied by the matrix.
- `ans.mtx`: The expected result of the multiplication, used for comparison.

## Compilation and Execution
To compile the project, use the provided Makefile:
```bash
make
./spmv A.mtx x.mtx result.mtx
```

## Functions Implemented
- `convert_coo_to_csr(row_ind, col_ind, val, m, n, nnz, &csr_row_ptr, &csr_col_ind, &csr_vals)`: Converts a matrix from COO format to CSR format.
- `spmv(csr_row_ptr, csr_col_ind, csr_vals, m, n, nnz, vector_x, res)`: Multiplies a sparse matrix (in CSR format) by a vector and stores the result.

## Testing
To test the implementation, use the input files in the test1 and test2 directories:
- `A.mtx`: The sparse matrix.
- `x.mtx`: The input vector.
- `ans.mtx`: The expected output vector.
Run the program and use the diff command to compare your result with ans.mtx:
```bash
diff result.mtx ans.mtx
```
Small differences in the last few digits are acceptable due to floating-point precision errors.

## Future Plans
- **Optimize Memory Usage**: Investigate further optimizations for memory usage, especially for very large matrices.
- **Parallelization**: Implement parallel processing to improve performance on large-scale matrix computations.
- **Support More Formats**: Extend the program to support other sparse matrix formats such as Compressed Sparse Column (CSC).