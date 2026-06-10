# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.huynt@vinuni.edu.vn
**Student ID:** 2A202600764
**Name:** Nguyen Thanh Huy

---

## Mo ta

Bai lab xay dung mot ETL Pipeline tu dong doc du lieu JSON, kiem tra chat luong (validation), bien doi du lieu (transform), va luu ket qua ra CSV. Ngoai ra, thi nghiem stress test voi Clean Data vs Garbage Data de hieu ro tam quan trong cua Data Quality doi voi he thong AI.

Cac buoc chinh:

- **Extract**: Doc du lieu tu `raw_data.json`
- **Validate**: Loai bo records co `price <= 0` hoac `category` rong
- **Transform**: Tinh `discounted_price = price * 0.9`, chuan hoa category sang Title Case, them timestamp
- **Load**: Luu ket qua ra `processed_data.csv`

---

## Cach chay (How to Run)

### Prerequisites

```bash
pip install pandas pytest
```

### Chay ETL Pipeline

```bash
python solution.py
```

Ket qua: file `processed_data.csv` se duoc tao ra voi cac records hop le.

### Chay Agent Simulation (Stress Test)

```bash
# Tao garbage data
python generate_garbage.py

# Chay agent voi clean data va garbage data
python agent_simulation.py
```

### Chay Tests

```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script chinh
├── raw_data.json            # Du lieu nguon
├── processed_data.csv       # Output sau khi chay pipeline
├── generate_garbage.py      # Tao garbage data cho stress test
├── agent_simulation.py      # Simulate AI Agent voi 2 loai du lieu
├── experiment_report.md     # Bao cao ket qua thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records doc vao:** 5
- **Records hop le (giu lai):** 3 (Laptop, Chair, Monitor)
- **Records bi loai:** 2 (Mystery Box co gia am, Phone co category rong)
- **discounted_price:** giam 10% so voi price goc
- **processed_at:** timestamp luc chay pipeline
