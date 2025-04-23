# BuddyAllocator

Buddy Allocator is a program using buddy memory allocation written in C for EECS 678 (Operating Systems). 

This project is meant to build familiarity with Buddy Memory Allocation, the memory algorithm, and memory. Kernel needs to allocate memory for user-level applications and the kernel itself. For 
user-level applications, it allocates a fixed size page frame at the time of each page fault. For kernel’s own allocations---such as allocating DMA buffers---it may need to allocate multiple
physically contiguous page frames. To serve these requirements, Linux kernel implements an allocator based on the buddy algorithm.

---
## 📝 Authors

Ellia Morse

Dev Patel

---

## 💾 Installation

To build the buddy allocator:
```bash
make
```

To generate documentation in HTML/LaTeX:
```bash
make doc
```

To clean the project use:
```bash
make clean
```

---

## 🚀 Usage

To run the executable use:
```bash
./buddy < test-files/test_sample1.txt
```

Or:
```bash
./buddy -i test-files/test_sample1.txt
```

---

## ✅ Features

Quash implements the following:

🧠 [**ALLOCATION**]
On a memory request, the allocator returns the head of a free-list of the matching size (i.e., smallest block that satisfies the request). If the free-list of the matching block size is empty, then a larger block size will be selected. The selected (large) block is then splitted into two smaller blocks. Among the two blocks, left block will be used for allocation or be further splitted while the right block will be added to the appropriate free-list.
```bash
void* buddy_alloc (int size);
```


🔎 [**Free**]
Whenever a block is freed, the allocator checks its buddy. If the buddy is free as well, then the two buddies are combined to form a bigger block. This process continues until one of the buddies is not free.
```bash
void buddy_free(void *addr)
```
---
## 🧪 Testing

Run all tests with:
```bash
make test
```

Or manually:
```bash
./run_tests.sh
```
---

## 🎯 Grading Breakdown
10% per working test file provided. 12 test files we may use for grading.
