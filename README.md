# Memory_Allocation

In this project, you will learn about Memory management. This project requires you to implement two memory allocation/de-allocation schemes, specifically Buddy System and Slab Allocation. The functioning of each of these schemes has been discussed in class. One of the jobs of the memory management subsystem is to service memory requests by matching the size of the request with a large enough hole, from which to satisfy the request. You will be given the starting address from where memory is to be allocated ( start_of_memory pointer) together with the size of this memory region ( mem_size = 1 MB). 

To implement the allocation policies, you should implement the following three interfaces in a file called my_memory.c , whose semantics are described below.

void setup(int malloc_type, int mem_size, void* start_of_memory);
The purpose of setup() is to perform any initialization of variables that you may need, specify and give you the pointer (start_of_memory) to the total amount of memory at your disposal, and also specify the type of memory allocator.
The parameter malloc_type will be either 0 or 1, denoting 0-Buddy System and 1-Slab Allocation.
void* my_malloc(int size); // returns a pointer to the allocated memory
This function should allocate size bytes of memory from that 1MB chunk of memory that is available for you (using the start_of_memory pointer) using the specified allocation algorithm. On allocation, it returns a pointer to the start of allocated memory. If a request cannot be accommodated by the scheme, this function should return -1. Note that the user programs expect that all the size bytes, starting from the first byte pointed to by the returned pointer, is available to it.
void my_free(void* ptr);
This function deallocates the memory segment being passed by the pointer. Note that when free-ing, the resulting free segment should be merged with relevant neighboring holes (as per the algorithm/scheme) whenever possible to create holes of larger size. No size argument is being explicitly passed in this call.
