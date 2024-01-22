CSC 360: Operating Systems (Fall 2023)

Programming Assignment 3: A Simple File System (SFS)

Date: Nov.19, 2023

Author: Hannah Wang, hannahwangmb@uvic.ca, V01015199

Usage:
    make
    ./diskinfo <test.img>
    ./disklist <test.img> </subdir1/subdir2/...>
    ./diskget <test.img> </subdir1/subdir2/source_filename> <output_filename>
    ./diskput <test.img> <source_filename> </subdir1/subdir2/dest_filename>

Design:
    
    diskinfo: Print out the super block and FAT info

    disklist: Print out the specified directory file list

    diskget: Copy file from specified file system path to current directory

    diskput: Copy file from current directory to specified file system path