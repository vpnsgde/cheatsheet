# Bash Shell Mastery Cheat Sheet

## 1. Cơ bản về Bash

``` bash
#!/bin/bash        # Shebang: chạy script bằng bash
set -e             # Dừng script khi gặp lỗi
set -u             # Lỗi khi dùng biến chưa khai báo
set -o pipefail    # Lỗi khi bất kỳ lệnh nào trong pipeline fail
set -x             # Debug: in lệnh trước khi chạy
```

**Chạy script**

``` bash
bash script.sh
chmod +x script.sh && ./script.sh
```

## 2. Biến & Tham số

``` bash
name="John"
echo "Hello $name"       # Mở rộng biến
echo "Hello ${name}!"    # Cách an toàn

readonly var=value       # Chỉ đọc
unset var                # Xóa biến

# Tham số dòng lệnh
$0   # Tên script
$1   # Tham số 1
$@   # Tất cả tham số (giữ nguyên tách)
$*   # Tất cả tham số (ghép thành chuỗi)
$#   # Số tham số
"$@" # Luôn dùng khi lặp qua tham số

# Mặc định nếu rỗng
echo "${var:-default}"
```

## 3. Toán học & Kiểu dữ liệu

``` bash
((a = 5 + 3))
echo $a

# Cộng biến
((count++))
((count += 10))

# So sánh số
if (( a > b )); then echo "a > b"; fi
```

## 4. Cấu trúc điều khiển

``` bash
# If
if [[ $x -gt 5 ]]; then
    echo "Lớn hơn 5"
elif [[ $x -eq 5 ]]; then
    echo "Bằng 5"
else
    echo "Nhỏ hơn 5"
fi

# Case
case $var in
    start) echo "Bắt đầu";;
    stop)  echo "Dừng";;
    *)     echo "Không hợp lệ";;
esac

# For
for i in {1..5}; do
    echo "Loop $i"
done

# While
while read -r line; do
    echo "Dòng: $line"
done < file.txt
```

## 5. Xử lý chuỗi

``` bash
len=${#str}         # Độ dài
echo ${str:0:5}     # Cắt chuỗi
echo ${str#prefix}  # Xóa prefix
echo ${str%suffix}  # Xóa suffix
echo ${str/pattern/replace} # Thay thế
```

## 6. Mảng

``` bash
arr=(one two three)
echo ${arr[0]}
echo ${arr[@]}      # Tất cả phần tử
echo ${#arr[@]}     # Số phần tử

arr+=(four)         # Thêm phần tử
unset arr[1]        # Xóa phần tử
```

## 7. Xử lý file & thư mục

``` bash
[ -f file.txt ] && echo "Có file"
[ -d /path ]   && echo "Có thư mục"
[ -s file.txt ] && echo "Không rỗng"
[ -r file.txt ] && echo "Có quyền đọc"

cp src.txt dst.txt
mv old new
rm file.txt
mkdir -p dir/subdir
```

## 8. I/O & Redirection

``` bash
command > out.txt       # Ghi đè
command >> out.txt      # Ghi nối
command 2> err.txt      # Lỗi
command &> all.txt      # Cả output + error
command < in.txt        # Nhập từ file

# Pipe
cat file.txt | grep "pattern"
grep "pattern" file.txt | sort | uniq
```

## 9. Hàm

``` bash
myfunc() {
    local var="inside"
    echo "Function param 1: $1"
}
myfunc "Hello"
```

## 10. Mẹo Bash nâng cao

``` bash
# Lấy đường dẫn script
DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

# Kiểm tra lệnh tồn tại
command -v git >/dev/null || { echo "Git chưa cài"; exit 1; }

# Xử lý tên file có dấu cách
find . -type f -print0 | while IFS= read -r -d '' file; do
    echo "$file"
done
```

## 11. Tools thường dùng với Bash

  Tool              Chức năng
  ----------------- ---------------------------
  `grep`            Tìm kiếm theo pattern
  `awk`             Xử lý text dạng cột
  `sed`             Thay thế/chỉnh sửa chuỗi
  `cut`             Cắt cột
  `sort` + `uniq`   Sắp xếp và loại trùng
  `xargs`           Chuyển list thành tham số
  `parallel`        Chạy song song
  `jq`              Xử lý JSON
