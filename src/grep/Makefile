.PROGRAMM: all clean test check s21_grep
CFLAGS=-Wall -Werror -Wextra -std=c11 -D_GNU_SOURCE

all: s21_grep

s21_grep:
	gcc ${CFLAGS} s21_grep.c -o s21_grep

clean:
	rm -rf s21_grep s21_grep.dSYM log.txt RESULT_VALGRIND.txt

check: s21_grep
	cppcheck --enable=all --suppress=missingIncludeSystem *.c *.h
	python3 ../../materials/linters/cpplint.py --extensions=c *.c *.h
	CK_FORK=no valgrind --vgdb=no --leak-check=full --show-leak-kinds=all --track-origins=yes --verbose --log-file=RESULT_VALGRIND.txt s21_grep

test: s21_grep
	bash s21_test_grep.sh
	rm -rf log.txt