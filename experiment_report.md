# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600764
**Name:** Nguyen Thanh Huy
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                          | Agent Response                                                   | Accuracy (1-10) | Notes                                               |
| --------------------------------- | ---------------------------------------------------------------- | --------------- | --------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200.            | 9               | Ket qua dung, san pham electronics hop le           |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 1               | Sai hoan toan do outlier cuc doan lam nhiem du lieu |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung Garbage Data, Agent cho ra ket qua sai vi co nhieu van de chat luong du lieu nghiem trong.

Thu nhat, co Duplicate IDs: id=1 xuat hien 2 lan cho ca Laptop va Banana, khien he thong xu ly nham so luong san pham thuc te, gay ra tinh toan thong ke sai lech.

Thu hai, co Outlier cuc doan: Nuclear Reactor co gia $999,999 la mot gia tri bat thuong, cao hon rat nhieu so voi cac san pham thong thuong. Vi Agent tim gia cao nhat trong danh muc electronics, no chon Nuclear Reactor thay vi Laptop la lua chon hop ly hon. Day la van de outlier dien hinh anh huong truc tiep den logic nghiep vu.

Thu ba, du lieu co Wrong Data Types: gia san pham "ten dollars" la chuoi van ban thay vi so nguyen, co the gay loi khi thuc hien tinh toan so hoc hoac so sanh gia tri.

Thu tu, Null Values va gia bang 0 tao ra cac records vo nghia: Ghost Item khong co id va category la None, gia bang 0 cho thay day la du lieu khong hop le nhung van ton tai trong tap du lieu.

Nhung van de nay chung minh rang du lieu rac co the dan den ket qua hoan toan sai lech, bat ke logic cua Agent co tot den dau. Data Observability va ETL Validation la nen tang bat buoc cho moi he thong AI.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan.

Du lieu sach la nen tang cua bat ky he thong AI nao. Mot prompt tot khong the bu dap cho du lieu xau. Neu du lieu dau vao co loi nhu outliers, null values, wrong types hay duplicate records, ket qua dau ra cua Agent se luon sai lech. Vi the, buoc Validate trong ETL Pipeline khong phai tuy chon ma la bat buoc, giup loai bo nhung records co van de truoc khi du lieu duoc dua vao mo hinh AI.
