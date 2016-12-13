# R-Programming-Assingnment-2

makeCacheMatrix <- function(x = matrix()){  
m <- NULL  
set <- function(y){
x <<- y  
m <<- NULL #store matrix in cache
}
get <- function() x #get matrix
setInverse <- function(solve) m<<- solve #set inverse matrix
getInverse <- function() m #get inverse matrix
list(set = set, get = get,
setInverse = setInverse,
getInverse = getInverse)  ## create list of functions
}
## Write a short comment describing this function
## cacheSolve take a custom matrix type created by the makeCacheMatrix function
## and calculates the inverse matrix of it
## but first it checks to see if the calculation has been done before
## if it has been done before it recalls the data from the cache. If it has
## before it calculates the inverse matrix then store it in the cache
cacheSolve <- function(x, ...) {
## Return a matrix that is the inverse of 'x'
m <- x$getInverse()                 #query the x matrix's cache
if(!is.null(m)){                    
message("getting cached data")    # sent message indicating this is just cache
return(m)                         # return the cache  
}
data <- x$get()                     # get the matrix used by makeCacheMatrix
m <- solve(data, ...)               # calculate the inverse of the matrix
x$setInverse(m)                     

