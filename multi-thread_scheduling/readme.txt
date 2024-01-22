CSC 360: Operating Systems (Fall 2023)

Programming Assignment 2: Multi-Thread Scheduling (MTS)

Date: Oct.25, 2023
Resubmission Date: Nov.14, 2023
Author: Hannah Wang, hannahwangmb@uvic.ca, V01015199

Resubmission Version Changes:
	added a p2 directory in the tar.gz file, change the usage from 'input.txt' to argument[1]

Major Functions
a. printTimeDifference: to convert and print time in format HH:MM:SS.S
b. addToArrivalQueue: adding a train that has crossed the main track into arrival_order
c. printEastReady and printWestReady: print out trains that finished loading
d. enqueue: adding a train to appropriate addToArrivalQueue
e. trainThread: threads for trains, start running when been signaled, after loading time, call enqueue()
f. printMainTrack: print out the train ON/OFF the main track message using printTimeDifference(), call addToArrivalQueue(), update queues(remove crossed trains)
g. controllerThread: use to controll which train in the ready queues should go on the main track
h. main: store input file data, create threads, signal trainThread when all threads have been created


Code Design
1. count the number of total trains, create threads for each of them
2. when all threads are created, main() broadcast, all trains start loading at the same time
3. after loading, trains adding into respective queue, one mutex is using here to lock one queue at a time preventing multiple threads are adding into the same queue at a time, while allowing multiple threads adding into different queues at a time.
4. create another controller thread to manage which train should go first according to the rules in assignment description
5. once the next train is decided, call printMainTrack() to print out the crossing message
6. after crossing the main track, add the train to the arrival_order and remove from the original queue
7. since only one controller thread is managing the main track, we don't have to use any mutex here
8. the controller thread will keep assigning trains until arrival_count is equal to total_trains


Usage: Put mts.c, Makefile, inputfile under the same directory, then
    make
    ./mts inputfile

Input file example:
e 10 6
W 6 7
E 3 10
