# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-0343
**Name:** Vũ Minh Khải
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. |10 | Agent chọn đúng sản phẩm tốt nhất|
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 1| Agent bị đánh lừa bởi dữ liệu bẩn Nuclear Reactor có trong dữ liệu. Logic của agent là sản phẩm đắt nhất là sản phẩm tốt nhất. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?
Agent trả lời sai khi dùng dữ liệu ở garbage_data.csv vì logic của nó. Agent mặc định rằng sản phẩm đắt nhất là sản phẩm tốt nhất. Logic này hoạt động đúng nếu dữ liệu đầu vào đã được xử lý và làm sạch. Trong khi dữ liệu garbage_data.csv bẩn, chưa được xử lý, chứa giá trị ngoại lại Nuclear Reactor

- **Duplicate IDs:** Có 2 record có id = 1, phá vớ unique ở id. Giả sử 
- **Outliers:** Record "Nuclear Reactor" giá $999999, cái này ảnh hưởng đến câu trả lời cuối, agent quét tìm giá cao nhất sau đó trả về giá trị ngoại lai này.
- **Wrong data types:** Cột price chứa "ten oollars" là chuỗi trong khi cột này yêu cầu số. Có thế dẫn đến các phép toán, so sánh,... trong pandas bị crash hoặc cho kết quả sai.
- **Null values:** Record "Ghost Item" có id = None và category = None, có thể gây lỗi khi lọc theo id, category hoặc khi thực hiện tính toán
---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Đồng ý. Một prompt được viết hoàn hảo vẫn khiến agent cho ra kết quả sai nếu dữ liệu đầu vào của agent chứa các thông tin không chính xác do dữ liệu bẩn.
