# Copyright (C) 2014, 2016 International Business Machines Corporation  
# All Rights Reserved      

# NOTE: To compile, you must have HBASE_HOME and HBASE_HOME set in your
# environment.

.PHONY: all clean 

TOOLKIT_NAME=com.ibm.streamsx.hbase
STREAMS_HBASE_TOOLKIT ?= $(shell  ([ -e ../../$(TOOLKIT_NAME)/toolkit.xml ] && echo ../../$(TOOLKIT_NAME)) ||\
						          ([ -e "../$(TOOLKIT_NAME)" ] && echo ../$(TOOLKIT_NAME)) ||\
									echo $(STREAMS_INSTALL)/toolkits/$(TOOLKIT_NAME))


SPLC_FLAGS ?= -a --data-directory data 
SPLC = $(STREAMS_INSTALL)/bin/sc

SPL_CMD_ARGS ?= -t $(STREAMS_HBASE_TOOLKIT)
SPL_MAIN_COMPOSITE = com.ibm.streamsx.hbase.sample::PutRecord

all: data
	$(SPLC) $(SPLC_FLAGS) -M $(SPL_MAIN_COMPOSITE) $(SPL_CMD_ARGS) --output-dir output/PutRecord

data:
	mkdir data

clean: 
	$(SPLC) $(SPLC_FLAGS) -C -M $(SPL_MAIN_COMPOSITE) --output-dir output/PutRecord
	rm data/*.out

