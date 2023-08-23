# Login
```
ssh Mssv@kagayaki
```
Ví dụ:
```
ssh s2120443@kagayaki
```
# Xin Queue để chạy
```
qsub -q GPU-1 -I
```
# Load module GPU
```
Module load cuda
```
# Delete screem
```
$ screen -X -S [session # you want to kill] quit
```

# Export the environment of conda
```
conda env export > environment.yml
```
