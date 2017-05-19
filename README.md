# DGIM
Problem
– Given a stream of zeroes (0's) and ones (1's),
– Count a number of ones in the last k bits

DGIM algorithm
– Query answering
● How many 1's there are in the last k bits (k ≤ N)
– Procedure (O(logN))
● Sum sizes of all buckets but the last
– Last bucket → bucket with the earliest timestamp that includes at least
some of the k most recent bits
● Add half the size of the last bucket

DGIM algorithm
– Maintaining buckets
● When a new bit comes in
– delete the oldest bucket if its end-time is prior to N time units before the
current time (update LAST/TOTAL)
– If the new bit is 0 → no other changes
– If the new is is 1
● Create new bucket with size 1 (for the new bit) and current
timestamp (TOTAL++)
● Count number of buckets with size 1
● If there are 3 buckets of size 1 → merge oldest two into single
bucket of size 2
● If there are 3 buckets of size 2 → merge oldest two into single
bucket of size 4
● … (update LAST)