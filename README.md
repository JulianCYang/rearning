# rearning
useful stuff

#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <stdbool.h>

// total number of lines, words, chars (if multiple files are input)
static int total_lines = 0, total_words = 0, total_chars = 0;
void wc(FILE *infile, char *inname);

int main(int argc, char *argv[]) {
    char *fname;
    FILE *file;
    if(argc > 1) {
	int counter;
        for (counter = 1; counter < argc; counter++){
	    fname = argv[counter];
	    file = fopen(fname,"r");
	}	
	wc(file,fname);
	
	
        // TODO: get the filename/s from argv, open each and pass it to wc
        
        if(argc > 2) { // print totals for multiple files
            printf("%7d %7d %7d   %s\n",  total_lines, total_words, total_chars, "total");
        }
        
    } else {
        // TODO: no arguments, process input from stdin
    }
    
    return 0;
}

void wc(FILE *infile, char *inname) {
    int lines = 0, words = 0, chars = 0;
    int c;
    size_t n = 0;
    char *code;
    fseek(infile, 0, SEEK_END);
    long file_size = ftell(infile);
    fseek(infile, 0 , SEEK_SET);
    code = malloc(file_size);
    if(infile == NULL)
	return NULL;
	
    while ((c = fgetc(infile)) != EOF) {
        code[n++] = (char)c;
    }
    code[n] = '\0';
    // TODO: read the file character by character and count the
    //       number of lines, words, and characters.
    chars = code;
    total_lines += lines;
    total_words += words;
    total_chars += chars;
    printf("%7d %7d %7d   %s\n",  lines, words, chars, inname);
}
