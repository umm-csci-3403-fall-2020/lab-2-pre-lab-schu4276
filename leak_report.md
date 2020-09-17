# Leak report

the function `is_clean` is allocating memory to the `cleaned` variable, and returning it back.  The memory for `cleaned` can't be freed before it exists because that would invalidate the function.
So, instead, we have to go to the end of the function. where `cleaned` will no longer be used. (I chose to do this right before the return statement. and do a ```free(cleaned);```.  It is also important to not the `if` statement that was added before the ```free()```.  This is needed to avoid freeing a statically allocated string, which does not use malloc/calloc.
