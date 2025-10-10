##
## EPITECH PROJECT, 2025
## new_workspace_creator
## File description:
## Makefile
##

CC      ?= gcc

SRC     = src/main.c

OBJ     = $(SRC:.c=.o)

NAME    = binary

LIBS	=	lib/libcli
			lib/libconf		\
			lib/libcore		\
			lib/libds		\
			lib/libio		\
			lib/liblog		\
			lib/libmem		\
			lib/libnet		\
			lib/libtest		\

LIB_FILES = $(foreach dir,$(LIBS),$(wildcard $(dir)/*.a))

LDFLAGS = $(foreach lib,$(LIB_FILES), -L$(dir $(lib)))

LDLIBS  = $(foreach lib,$(LIB_FILES), -l$(patsubst lib%.a,%,$(notdir $(lib))))

VPATH = include

CPPFLAGS = -iquote $(VPATH) \

CFLAGS += -Wall -Wextra -pedantic-errors -std=c2x -Werror

do-%:
	@for dir in $(LIBS); do 			 \
		$(MAKE) -C $$dir $* || exit $$?; \
	done

all: do-all $(NAME)

$(NAME): $(OBJ)
	$(CC) -o $(NAME) $(OBJ) $(LDFLAGS) $(LDLIBS)

clean: do-clean
	$(RM) $(OBJ)

fclean: do-fclean
	$(RM) $(NAME)

re: fclean all

debug: CFLAGS += -g3
debug: do-debug re

tests_run:
	@echo "hi"

.PHONY: all clean fclean re debug tests_run do-%
