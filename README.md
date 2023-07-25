Welcome to [Arcion](http://arcion.io) demo kit.
Arcion replicates data from one platform to another.
The demo kit makes testing and demo of Arcion easy.

# Install the Arcion demo kit  

Cut and paste the following in a terminal.

- run the latest
```
/bin/bash -c "$(curl -k -fsSL https://raw.githubusercontent.com/arcionlabs/docker-dev/HEAD/install.sh)"
```

- to run a specific tag
```bash
export ARCION_WORKLOADS_TAG=23.07
/bin/bash -c "$(curl -k -fsSL https://raw.githubusercontent.com/arcionlabs/docker-dev/${ARCION_WORKLOADS_TAG:-HEAD}/install.sh)"
```

# About the Arcion demo kit  

The diagram below describes the components of the demo kit.  Please refer to [https://docs.arcion.io](https://docs.arcion.io) for more info.

- Load Generator
- Data source
- Arcion host with dedicated metadata database
- Data destination

```mermaid!
graph LR
    L[Load Generator<br>TPC-C<br>YCSB] --> S
    subgraph Arcion Cluster
        A1
        M[(Meta <br>Data)]
    end
    S[(Source <br>Data)] --> A1[Arcion <br> UI]
    A1 --> T[(Destination<br>Data)]
```

# Prerequisites

Assumptions:

- Running on Windows WSL2, Liunx or Mac 
  - Intel CPU can run all databases
  - Apple Silicon cannot run Oracle 
- Have Arcion License or `replicant.lic`
  - `replicant.lic` file in the current directory 
  - `ARCION_LICENSE` env variable    
- Have Docker 19.3.0 or above
- Have `docker compose` or `docker-compose` 
- Have git installed
- Have access to a terminal
- Have access to a browser


[![asciicast](https://asciinema.org/a/587770.svg)](https://asciinema.org/a/587770)

# Recordings of the Demo

Arcion support snapshot, real-time, snapshot, and delta-snapshot replication modes.
Recorded Arcion CLI demos of source, destination, and replication type combination is available.
The recordings use `asciiinema` so that YAML config files used can be cut / pasted.
This is functional demo using TPCC and YCSB.
The data size is 1GB each, 1 thread on given to Arcion, and 8 GB of RAM shared.  

- Left side of the table (the left column) is the source.
- Right side of the table (the top row) is the destination.
- The cell has workloads and URL to the demo.
- A blank cell means a demo has not been recorded as of yet.
   
## Snapshot Replication CLI Demos

snapshot | kafka | minio | mysql | null | oracle | pg | redis stream | snowflake
-- | -- | -- | -- | -- | -- | -- | -- | --
db2 luw | [TPCC, YCSB](https://asciinema.org/a/596930) | [TPCC, YCSB](https://asciinema.org/a/596933) | [TPCC, YCSB](https://asciinema.org/a/596925) | [TPCC, YCSB](https://asciinema.org/a/596934) | [TPCC, YCSB](https://asciinema.org/a/596927) | [TPCC, YCSB](https://asciinema.org/a/596926) | [TPCC, YCSB](https://asciinema.org/a/596929) | [TPCC, YCSB](https://asciinema.org/a/596928)
informix | [TPCC, YCSB](https://asciinema.org/a/596949) | [TPCC, YCSB](https://asciinema.org/a/596417) | [TPCC, YCSB](https://asciinema.org/a/596950) | [TPCC, YCSB](https://asciinema.org/a/596416) | [TPCC, YCSB](https://asciinema.org/a/596952) | [TPCC, YCSB](https://asciinema.org/a/596953) | [TPCC, YCSB](https://asciinema.org/a/596955) | [TPCC, YCSB](https://asciinema.org/a/596415)
mysql | [TPCC, YCSB](https://asciinema.org/a/596940) | [TPCC, YCSB](https://asciinema.org/a/596938) | [TPCC, YCSB](https://asciinema.org/a/596941) | [TPCC, YCSB](https://asciinema.org/a/596942) | [TPCC, YCSB](https://asciinema.org/a/596943) | [TPCC, YCSB](https://asciinema.org/a/596937) | [TPCC, YCSB](https://asciinema.org/a/596948) | [TPCC, YCSB](https://asciinema.org/a/M27aYd5QkOStjN80Pdqx2hBCc)
oracle | [TPCC, YCSB](https://asciinema.org/a/596635) | [TPCC, YCSB](https://asciinema.org/a/596638) | [TPCC, YCSB](https://asciinema.org/a/596642) | [TPCC, YCSB](https://asciinema.org/a/596643) | [TPCC, YCSB](https://asciinema.org/a/596958) | [TPCC, YCSB](https://asciinema.org/a/596641) | [TPCC, YCSB](https://asciinema.org/a/596957) | [TPCC, YCSB](https://asciinema.org/a/596634)
pg | [TPCC, YCSB](https://asciinema.org/a/596959) | [TPCC, YCSB](https://asciinema.org/a/596960) | [TPCC, YCSB](https://asciinema.org/a/596962) | [TPCC, YCSB](https://asciinema.org/a/596963) |   | [TPCC, YCSB](https://asciinema.org/a/596961) |   | [TPCC, YCSB](https://asciinema.org/a/596966)



## Full Replication CLI Demos

full | databricks | Google Cloud Storage | Google CloudSQL MySQL | kafka | minio | mongodb | mysql | null | oracle | pg | redis stream | singlestore | snowflake | sqlserver
-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --
db2 luw |   |   |   |   |   |   | [TPCC YCSB](https://asciinema.org/a/597115) |   | [TPCC YCSB](https://asciinema.org/a/597114) | [TPCC YCSB](https://asciinema.org/a/597116) |   |   |   |  
IBM Db2 |   |   |   |   |   |   |   |   | [various](https://youtu.be/TYXJhwjXIms) |   |   |   |   |  
informix |   |   |   | [YCSB](https://asciinema.org/a/596970) | [YCSB](https://asciinema.org/a/596971) |   | [YCSB](https://asciinema.org/a/596959) | [YCSB](https://asciinema.org/a/596973) | [YCSB](https://asciinema.org/a/46fe1mFKWyIvRhSaqEnIrGacN),[YCSB](https://asciinema.org/a/596974) | [YCSB](https://asciinema.org/a/596418),[YCSB](https://asciinema.org/a/596975) | [YCSB](https://asciinema.org/a/596977) |   | [YCSB](https://asciinema.org/a/596402) |  
mongodb |   |   |   |   |   | [](https://youtu.be/33TBVqFDuCk) |   |   |   |   |   |   |   |  
mysql | [various](https://youtu.be/ytKpvWJi3Lo) | [TPCC YCSB](https://asciinema.org/a/597274) | [TPCC YCSB](https://asciinema.org/a/597663) | [TPCC YCSB](https://asciinema.org/a/596184) | [TPCC YCSB](https://asciinema.org/a/596183) |   | [TPCC YCSB](https://asciinema.org/a/596980),[TPCC & YCSB](https://asciinema.org/a/597442),[TPCC & YCSB](https://asciinema.org/a/597443) | [TPCC YCSB](https://asciinema.org/a/596979) | [TPCC YCSB](https://asciinema.org/a/596981) | [TPCC YCSB](https://asciinema.org/a/587771) | [TPCC YCSB](https://asciinema.org/a/596982) | [various](https://youtu.be/x9_ccBjf1EQ) | [](https://asciinema.org/a/8CO7i2Ecj8jPdSh4mFOfDbm9F) |  
oracle | [](https://youtu.be/SAc7v7ZspPw) |   |   | [TPCC YCSB](https://asciinema.org/a/596653),[TPCC YCSB](https://asciinema.org/a/596984) | [TPCC YCSB](https://asciinema.org/a/596652) | [various](https://youtu.be/sK3tZmpb1YI),[](https://youtu.be/dTChAc9GpSc) | [TPCC YCSB](https://asciinema.org/a/596647) | [TPCC YCSB](https://asciinema.org/a/596644) | [various](https://youtu.be/sVhraqx095g) | [TPCC YCSB](https://asciinema.org/a/596651) |   | [various](https://youtu.be/x9_ccBjf1EQ) | [YCSB](https://asciinema.org/a/596633),[](https://youtu.be/XRAFNrhv5cI) |  
pg |   |   |   | [YCSB](https://asciinema.org/a/598279) | [YCSB](https://asciinema.org/a/598285) |   | [YCSB](https://asciinema.org/a/598277) |   | [X](https://asciinema.org/a/598282) | [YCSB](https://asciinema.org/a/598284) | [YCSB](https://asciinema.org/a/598286) |   |   | [YCSB](https://asciinema.org/a/598281)
snowflake |   |   |   |   |   |   |   |   |   |   |   |   |   | [various](https://youtu.be/8sn8KJfh9ns)


