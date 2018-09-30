# clion
1. 透過官網申請免費學生授權(1年期) https://www.jetbrains.com/student/  
2. 透過官網下載CLion https://www.jetbrains.com/clion/download/  
3. 安裝時輸入申請的帳號密碼即可獲得授權

```bash
sduo apt install gcc
sudo apt install g++
sudo apt install make
```
## 設定遠端同步
1. 確認可ssh至遠端機器
```clion
Tools > Deployment > Configuration >
左上角「+」號 > 輸入好記名稱 > Type: SFTP
選擇該機器 按下左上角的打勾 此時機器會變成粗體
```
```clion
Connection > SFTP host: 遠端機器IP > Port: 遠端機器Port(預設22) >
User name, Password: 輸入使用者帳號密碼
```
```clion
Mappings > Local path: 指定本機資料夾 > Deployment path...: > 指定遠端料夾
```
```clion
Tools > Deployment > Options > Exclude items...: 新增;cmake-build-debug;CMakeLists.txt
Tools > Deployment > Automatic Upload(打勾)
```
## MPI
```bash
sudo apt install mpich

```
CMakeLists.txt add at line #5
```CMakeLists.txt
find_package(MPI REQUIRED)
include_directories(/usr/include/mpi)

SET(CMAKE_C_COMPILER  mpicc)
SET(CMAKE_CXX_COMPILER  mpicxx)
```
```clion
Run > Edit Configurations > 專案名稱 > Executable: /usr/bin/mpirun
Program arguments: -np 4 /專案路徑/專案執行檔
```
