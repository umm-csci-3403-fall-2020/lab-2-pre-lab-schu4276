# Leak report

the function is cleaned is allocating memory to the cleaned variable, and and returning it back.  The momory for cleaned cant be freed befor eit exists because that would invalidate the function. 
So, instead, we have to go to the end of the function. where cleaned will no longer be used before. (I chose to do this right before the return statement. and do a free(cleaned);
