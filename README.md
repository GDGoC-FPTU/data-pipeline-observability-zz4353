[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572429&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** vmkqa2@gmail.com
**Name:** Vũ Minh Khải
**Student ID:** AI20K-0343
---

## Mo ta

- Cài đặt các nội dung về Extract, Validate, Transform, Load
- Làm thực nghiệm so sánh kết quả khi chạy agent mô phỏng với dữ liệu sạch và khi chạy agent mô phỏng với dữ liệu bẩn

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Mo ta cach ban chay thi nghiem Clean vs Garbage data
```
Sử dụng code chạy đã được setup sẵn:
- Agent mô phỏng hoạt động bằng cách lọc những sản phẩm có category là electronics. 
- Chọn sản phẩm có giá cao nhất để đề xuất (logic: giá cao nhất -> sản phẩm tốt nhất)
---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Đã xử lý 5 records, 3 records được chọn và 2 records bị loại.
- Chạy thử agent simulation bằng data đã xử lý và data bẩn.
    - Kết quả: agent sử dụng dữ liệu bẩn đưa ra kết quả sai, agent sử dụng dữ liệu đã xử lý đưa ra kết chính xác. 
