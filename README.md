This code is the sample code provided for the Blue Waters Sustained Petascale Computing, Petascale Computing Institute 2019 seminar.  
[bluewaters.ncsa.illinois.edu/petascale-computing-2019](bluewaters.ncsa.illinois.edu/petascale-computing-2019)

Compiler Wrappers:  
    C - mpicc test.c -o test  
    C++ - mpicxx test.cpp -o test  
    FORTRAN - mpifort test.f90 -o test  
Link other libraries:  
    Math ex.  
    mpicc test.c -o test -lm  

Compiling on Cray Systems:  
    C - cc test.c -o test  
    C++ - c++ test.cpp -o test  
    FORTRAN - ftn test.f90 -o test  
Link other libraries on Cray:  
    Math ex.  
    cc test.c -o test -l  
    Cray MPI Libraries are automatically linked  

Running MPI Program  
    16 processes on a local node  
        mpiexec -n 16 ./test  
    16 processes on 4 nodes (each node has 4 cores)  
        mpiexec -hosts h1:4,h2:4,h3:4,h4:4 -n 16 ./test  
    Run the first 4 processes on h1. Next 4 on h2, etc  
        mpiexec -hosts h1,h2,h3,h4 -n 16 ./test  
    With lots of nodes a hostfile may be simpler  
        >cat hf  
            h1:4  
            h2:2  
        >mpiexec -hostfile hf -n 16 ./test  

Running MPI Program on Cray System  
    aprun -n 16 ./test  
