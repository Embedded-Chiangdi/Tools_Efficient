CC := gcc 
CC := ${CC}
BASE = ${shell pwd}
#ALL_MODULES_MK=${shell find ${BASE} -name "*.txt" -printf "%f "}
#ALL_MODULES=${ALL_MODULES_MK:.txt=}
all:
	@echo ${CC}
	@echo ${BASE}
	@echo "Now move to test1 and make"
	$(MAKE) -C test1
	$(MAKE) -C test1 install
	@echo "Now move to test1 and multi-make "
	$(MAKE) -C test2 -f ${BASE}/test2/t1.mk all
	$(MAKE) -C test2 -f ${BASE}/test2/t2.mk all
	$(MAKE) -C test2 -f ${BASE}/test2/t2.mk all
#	@mkdir -p ${BASE}/test 	test1 test2
#	@echo ${ALL_MODULES}