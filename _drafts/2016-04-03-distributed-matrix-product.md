---
published: false
layout: post
title: Distributed Matrix product
date: 2016-04-03T11:10:00.000Z
categories: "Computer-Science"
---


Matrix multiplication is something a mathemacial operation that takes two matrices and produces another one as a result. Before explaining how distributed matrices product can work, we are going to do a quick reminder of whati is a matrix and what's a dot product of matrices. You can skip that part if everything is fresh in your mind.

## Matrices and dot product

### Matrices
A matrix is a data structure that's made of columns and rows. It is basically a Tic tac toe grid with a potentially infinite number of rows and columns and numbers within the grid. 

// Paste here the images about tic tac toe

When a matrix has the same number of rows and column we say that it is squared ... because it looks like a square.

// Square matrix

### Dot Product
A dot product an operation that takes two matrices and return another matrix as the result. Let's take an example to go through the process. 

Let A be a squared 2x2 (2 rows & 2 columns) matrix and B another squared 2x2 matrix.

// Paste here the image of A and B

This matrix product will result in another 2x2 matrix C

// Matrix c image

In that configuration each element of C: c(1,1), c(1,2), c(2,1) and c(2,2) is the result of sums and products on the corresponding rows of A and columns of B with the following fashion:

* c(1,1) = 1 * 2 + 3 * 3 = 11
* c(1,2) = 1 * 1 + 3 * 1 = 4
* c(2,1) = 5 * 2 + 2 * 3 = 16
* c(2,2) = 5 * 1 + 2 * 1 = 7

The overall operation look like this, in red is circled the elements of the matrix involved in getting the c(1,1) = 11 part of the resulting matrix C:

// Paste the image of the dot product

## Distributed matrix product

Why trying to distribute this operation accross processors?

This operation is used in a lot of Machine Learning algorithms. The more data you have in machine learning, the better the output of your algorithm is likely to be. So we want to be able to make that operation on very large matrices that potentialy don't fit into memory.

For the sake of simplicity we will consider squared matrices but everything can be generalized to all kind of matrices.

### Column/Row data segmentation

Since our main problem is to be able to store the whole matrices data into memory on one processor we will have to distribute it.

Let p be the number of processors we can use.

A first way to do that is to split the first matrix in p slices of rows and split B in p slices of columns.

// Insert image of A and B sliced

Let's attribute each slice of the data for each matrix to a processor. What happens in processor 1 ?

It gets the first rows slice of A and the first column slice of B. With that, and using the definition of the dot product, it is only able to compute a specific part of C, the top left corner of C.

//insert image of C

Follwing that logic, each processor will be able to compute a part of the diagonal on C. Resulting in a partial result of the dot product for C. The only elements that we will be able to compute will the the blacked squared elements on the following drawing.

// Drawing with the C diagonal

In order to fill the blanks we will iterate but we will change how the slice of B are affected to processors. Now processor one will have rows' slice 1 of A and columns slice 2 of B and will be able to compute the corresponding part of C, which is the intersection of slice 1 and 2. If we imagine the processors in a ring all they have to do at each iteration is pass their current slice of B to their neighboor untill everybody has seen all the slices of B.

// insert image of ring

The result will of the next iteration will be the parts of C drawn in red.

// Insert image of C with red

This really gives us the intuition that if we repeat that operation enough we will be able to compute the whole matrix after having computed small parts of it.

### Submatrices data segmentation







