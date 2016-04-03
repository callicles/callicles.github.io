---
published: false
layout: post
title: Distributed Matrix multiplication
date: 2016-04-03T11:10:00.000Z
categories: "Computer-Science"
---


Matrix multiplication is something a mathemacial operation that takes two matrices and produces another one as a result. Before explaining how distributed matrices product can work, we are going to briefly fly over what's a matrix and what's a dot product of matrices. You can skip that part if you already know about it.

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

