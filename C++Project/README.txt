Put all your sources into 'src/'' and all your headers into 'include/',
Inside those 2 directories you can create the directory tree you prefer, it will always compile.
To compile, simply run 'make' via shell or via sublime build system; The binaries are created inside the 'build/' directory.

PS: the standard extensions for source files is .cpp, and the standard extension for compiled objects is .o. You can freely make any
    changes in the makefile. I made it easy for you.
