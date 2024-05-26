hello_world: hello_world.o
# First generates hello_world.o because there is an implicit rule for
# converting between .c and .o files.
# Second, generate hello_world executable because there is an implicit rule for
# linking an executable from .o files


# Equivilent to
# hello_world: hello_world.o
# 	cc hello_world.o -o hello_world
# hello_world.o: hello_world.c
# 	cc -c -o hello_world.o hello_world.c
