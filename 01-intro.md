---
title: L01 - MapReduce
nav_order: 2
---

Go

50% - Lab
  - MapReduce
  - Raft
  - K/V Store - Fault Tolerant
  - Sharded K/V Store - Fault Tolerant
20% - 1 midterm
20% - final exam
10% - activity




Distibuted Systems
- Fault Tolerance
  - 1000 server - 3 failures a day
- Availabity
  - Replication - Sync/Async
    - Primary Node
	- Secondary Node(s)
- Graceful Degradation
- Recoverability
- Consistency
  - Network Partitioning -> Split Brain

Abstraction
 - Put(k, v)
 - Get(k)

GFS - Google File System
 - client library
   - Thin
   - Heavy

Storage
Compute
RPC - Remote Procedure Call

MapReduce - Distributed Compute Engine
  - Web Indexing
  - Log Processing
  - ...


Info {
  file_name,
  line,
}

01 [ a b
     cd e]
02 [ b c e ]
03 [a cd b ]

def map(info, line):
	for word in line.split(' '):
		emit(word, 1)

def reduce(pair):
	word = pair[0]
	counts = pair[1]
	emit(word, sum(counts))

(1, 2), (b, 3), (c, 1), (cd, 2)
(a, (1, 1)) -> (a, 2)
(b, (1, 1, 1)) -> (b, 3)
...
...

def map(info, line):
	for word in line.split(' '):
		emit(word, (info.file_name, info.line_number, column_number))

2
def reduce(pair):
	word = pair[0]
	page_infos = pair[1]
	emit(word, page_infos)

IdentityReducer



Data Procesing Engine
 - Batch - MapReduce
 - Streaming - Spark, Flume

Job - Count Works
Task - Map/Reduce
Worker - Tasks are scheduled
Server/Machine - Runs workers
Controller - Orchestrates Job

Struggler Worker

Layer
- Control Plane
- Data Plane
