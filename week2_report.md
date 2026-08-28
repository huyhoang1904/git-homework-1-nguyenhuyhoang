# Git Practice — Week 2

## Part A

### 1. Tạo và commit file `week2.md` trên nhánh `main`, sau đó tạo nhánh `week2`

```bash
touch week2.md

git add week2.md
git commit -m "commit week2.md"
git branch week2
git switch week2
```

### 2. Thêm nội dung vào `week2.md` trên nhánh `week2`

```bash
echo "working1" >> week2.md

git add week2.md
git commit -m "working1"

echo "working2" >> week2.md
git add week2.md
git commit -m "working2"
```

### 3. Thêm dòng mới và commit

```bash
echo "new line" >> week2.md

git add week2.md
git commit -m "add a new line"
```

**Nhận xét:** File `week2.md` trên nhánh `main` không có nội dung.

**Lý giải:**

- File `week2.md` được tạo ra và commit trên nhánh `main`. Lúc này file `week2.md` được tracked nhưng chưa có nội dung.
- Sau đó rẽ nhánh sang `week2` và thực hiện 3 commit. Tất cả các dòng text đẩy vào file `week2.md` đều chỉ được ghi nhận trên nhánh `week2`.
- Khi `git switch main`, Git khôi phục toàn bộ working directory về đúng trạng thái commit cuối cùng trên nhánh `main`, do đó những thay đổi trên nhánh `week2` sẽ bị ẩn đi.

### 4. Tạo nhánh `week2b`, merge `week2` vào và xóa nhánh `week2`

```bash
git switch -c week2b

git merge --no-ff week2
git branch -d week2
```

---

## Part B

### 1. Tạo nhánh `wip`, thêm file, sau đó merge `week2b` vào `main`

```bash
git switch -c wip

touch wip.txt
git add wip.txt
git commit -m "add wip.txt"

git switch main
git merge week2b
```

### 2. Ghi danh sách nhánh đã merge / chưa merge vào `week2.md`

```bash
echo -e "\n branch merged into main" >> week2.md
git branch --merged >> week2.md

echo -e "\n branch not merged into main" >> week2.md
git branch --no-merged >> week2.md

git add week2.md
git commit -m "add branch filter result in week2.md"
```

### 3. Xóa nhánh `week2b`

```bash
git branch -d week2b
```

### 4. Đổi tên nhánh `wip` thành `work-in-progress` và set upstream

```bash
git branch --move wip work-in-progress
git branch --set-upstream origin work-in-progress
```

---

## Part C

### 1. Thêm nội dung vào `wip.txt` trên nhánh `work-in-progress`

```bash
git switch work-in-progress

echo "hello world" >> wip.txt
git add wip.txt
git commit -m "add text to wip.txt"
```

### 2. Kiểm tra thông tin tracking branch

```bash
git branch -vv
```

### 3. Push nhánh lên remote và tạo Pull Request

```bash
git push origin work-in-progress
```

- Truy cập vào repo trên GitHub và chọn **"Compare and pull request"**.
- Chọn **"Create pull request"**.

---

## Part D

### 1. Tạo nhánh `experiment` với 2 commit

```bash
git switch main

git switch -c experiment
echo "file 1" > exp1.txt
git add exp1.txt
git commit -m "add exp1.txt"

echo "file 2" > exp2.txt
git add exp2.txt
git commit -m "add exp2.txt"
```

### 2. Thêm commit mới trên `main`

```bash
git switch main

echo "new file on main" > new_file.txt
git add new_file.txt
git commit -m "add new_file.txt to main"
```

### 3. Rebase `experiment` lên `main`

```bash
git switch experiment
git rebase main
```

### 4. Ghi giải thích về rebase vào `week2.md`

```bash
echo -e "\n### What happened during rebase?\nWhen rebasing the 'experiment' branch onto 'main', Git temporarily removed the new commits made on 'experiment' (exp1 and exp2). It then updated the base of the 'experiment' branch to point to the latest commit of 'main'. Finally, it reapplied those removed commits on top of the new base. This process rewrites the commit history into a clean, linear line instead of a diverged graph." >> week2.md

git add week2.md
git commit -m "add rebase explanation to week2.md"
```

### 5. Merge `experiment` vào `main`

```bash
git switch main
git merge experiment
```

### 6. Push `main` lên remote

```bash
git push origin main
```

### 7. Đã thực hiện ở mục 6.