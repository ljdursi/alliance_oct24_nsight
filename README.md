# alliance_oct24_nsight
Materials for NSight walkthrough for Alliance Federation Staff

Walkthrough taken from the [OpenHackathons HPC Profiler Tutorial](https://github.com/openhackathons-org/HPC_Profiler)

The commands we'll be running are:

```
module load cuda nvhpc
cd nsight_tutorail

cd lab1
make clean && make 
nsys profile -t nvtx --stats=true --force-overwrite true -o miniWeather_1 ./miniWeather
nsys-ui miniWeather_1.nsys-rep

cd ../lab2
make clean && make
nsys profile -t nvtx,openacc --stats=true --force-overwrite true -o miniWeather_2 ./miniWeather 400 200 200

cd ../lab3
make clean && make 
nsys profile -t nvtx,openacc --stats=true --force-overwrite true -o miniWeather_3 ./miniWeather 400 200 200

cd ../lab4
make clean && make
nsys profile -t nvtx,openacc --stats=true --force-overwrite true -o miniWeather_4 ./miniWeather 400 200 200

cd ../lab5
make clean && make
nsys profile -t nvtx,openacc --stats=true --force-overwrite true -o miniWeather_5 ./miniWeather
ncu --set full --clock-control=none -k regex:compute_tendencies_x --launch-skip 10 --launch-count 1 -f -o miniWeather1 ./miniWeather
ncu --set full --clock-control=none -k regex:compute_tendencies_x --launch-skip 100 --launch-count 1 -f -o miniWeather2 ./miniWeather 400 200 100
```

