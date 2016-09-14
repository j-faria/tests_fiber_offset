## Tests on the determination of the HARPS offset

These are the tests I did to make sure I am determining correctly the RV offset introduced by the change of fibers in HARPS.

Setting `t_fibers = 57170` and use the sampling from HD223854.  
Create a mock planet signal

    OPEN [7]: create
    INFO: Starting the planet creator
    How many planets? 1
    Specify the periods (y/N)?  y
    	period 1:  18
    Specify the eccentricities (y/N)?  y
    	eccentricity 1:  0
    Specify the semi-amplitudes (y/N)?  y
    	semi-amplitude 1:  50
    Use sampling from file (y/N)?  y
    Which file? /home/joao/phd/data/HD223854_harps.rdb
    Simply use sampling, error bars and number of points from file? Press n for other options (Y/n) 
    [1] Inject planet in data from file or [2] create from scratch? 2
    What type of noise? (no / W / r / wr) 
    
    INFO: Generating 1 planet(s)
        : -> sampling from /home/joao/phd/data/HD223854_harps.rdb
        : -> using errorbars from this file
        : -> 22 observations
        : -> white noise
    
    1.0
    Output to /home/joao/Work/OPEN/tmp4Awj3D


Read the file and add an offset of 19 m/s to the points after the fiber change.

    read tmp4Awj3D -d --skip=0 --nomps
    
    default.vrad[default.time > t_fibers] += 19e-3

Save to file `tmp4Awj3D_offset`.

## Results, data without offset

Using the data without offset, from file `tmp4Awj3D`, I obtain:

## Results, data with offset

Using the data **with** offset, from file `tmp4Awj3D_offset`, I obtain:
