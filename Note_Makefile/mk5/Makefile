.PHONY: all say_hello generate clean rename

all:say_hello generate

#.DEFAULT_GOAL := generate
Prefix = "re"

say_hello:
	@echo "Hello World" 
generate: 
	@echo "Creating empty files..."
	@touch file{1..10}.txt
rename:
	@echo "Rename files's name..."
	@for file in $(shell ls *.txt) ;\
	do\
		echo $${file}" changed";\
		mv $${file} ${Prefix}$${file};\
	done;
clean:
	@echo "Cleaning up ...."
	@rm *.txt
