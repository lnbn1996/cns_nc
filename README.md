# Template LaTeX Chuẩn QĐ 1799 — Đại học Cần Thơ (XeLaTeX)

Mẫu trình bày báo cáo khoa học / luận văn thạc sĩ dựa trên định dạng đã hiệu chỉnh chuẩn **Quyết định số 1799/QĐ-ĐHCT** và biên dịch bằng **XeLaTeX** để sử dụng trực tiếp font hệ thống **Times New Roman** (khớp 1:1 kích thước `bp` với Microsoft Word).

---

## Thông số định dạng đã thiết lập sẵn

- **Khổ giấy & Lề (QĐ 1799):** Khổ A4 đứng (`oneside`), lề trái `3.0 cm`, lề phải/trên/dưới `2.0 cm`, `headsep = 1.0 cm`, `footskip = 1.0 cm`.
- **Font chữ & Kích thước (`bp` chuẩn Word):**
  - Font chính: `Times New Roman` (hệ thống TrueType qua `fontspec`), chữ đơn cách `Courier New`, chữ không chân `Arial`, công thức toán `newtxmath`.
  - Văn bản thường & đề mục (`section`, `subsection`, `subsubsection`): **`13bp`** (các đề mục in đậm, thụt lề `1.0 cm`).
  - Tiêu đề chương (`chapter`): **`14bp`** in hoa, in đậm, căn giữa; Phụ lục dùng chữ thường đậm `14bp` căn giữa.
  - Chú thích Hình và Bảng: **`12bp`** chữ đứng thường (Bảng căn trái phía trên, Hình căn giữa phía dưới).
  - Bìa chính (`front_01_bia.tex`) & Bìa phụ (`front_01b_bia_phu.tex`, không logo): Khung viền đơn màu đen `2.5pt`, chữ chung `14bp`, tên đề tài tiếng Việt `20bp` in đậm, tên đề tài tiếng Anh `18bp` chữ đứng thường.
- **Giãn dòng & Khoảng cách (`setspace`):**
  - Phần đầu (`Tóm tắt`, `Abstract`, `Mục lục`, `Danh sách Bảng/Hình`) và nội dung chính (`Chương 1–5`): giãn dòng **`1.2`**, cách đoạn và đề mục **`6bp`**, thụt đầu dòng **`1.0 cm`**.
  - Danh sách liệt kê (`itemize`, `enumerate` với `[leftmargin=*]`): không chèn thêm khoảng cách thừa (`itemsep=0pt`, `parsep=0pt`, `topsep=0pt`).
  - **Giãn dòng `1.0`** tự động áp dụng cho: **Bảng (`table`, `longtable`)**, **Chú thích**, **Tài liệu tham khảo**, và toàn bộ **Phụ lục**.
- **Số trang:** Căn giữa phía dưới (`13bp`), không đánh số bìa, phần đầu dùng La-mã thường (`i, ii, iii...`), phần chính và Phụ lục đánh số Ả Rập từ `1`.

---

## Cấu trúc thư mục

```text
template_ctu_qd1799/
├── main.tex                          # File biên dịch chính (% !TEX program = xelatex)
├── .latexmkrc                        # Cấu hình tự động build bằng XeLaTeX + BibTeX
├── .gitignore                        # Bỏ qua file tạm khi dùng Git
├── references.bib                    # File tài liệu tham khảo mẫu (BibTeX)
├── images/
│   └── logoCTU.png                   # Logo Đại học Cần Thơ cho bìa chính
├── 00_frontmatter/
│   ├── front_01_bia.tex              # Trang bìa chính (có logo, khung đen 2.5pt)
│   ├── front_01b_bia_phu.tex         # Trang bìa phụ (không logo)
│   ├── front_02_xacnhan.tex          # Phiếu xác nhận / đánh giá (tùy chọn bật trong main.tex)
│   ├── front_03_camon.tex            # Lời cảm ơn (tùy chọn)
│   ├── front_04_tomtat_tiengviet.tex # Tóm tắt tiếng Việt
│   ├── front_05_abstract_tienganh.tex# Abstract tiếng Anh
│   ├── front_06_camdoan.tex          # Lời cam đoan (tùy chọn)
│   └── front_09_danhmuc_viettat.tex  # Danh mục từ viết tắt (longtable 12bp, 1.0)
├── chapters/                         # Các chương nội dung (mẫu 5 chương chuẩn QĐ 1799)
└── appendices/                       # Phụ lục 1, 2 (giãn dòng 1.0, đánh số trang từ 1)
```

---

## Hướng dẫn biên dịch

### 1. Dùng `latexmk` hoặc VS Code (LaTeX Workshop)
Thư mục đã có sẵn `.latexmkrc` (`$pdf_mode = 5;`) và dòng `% !TEX program = xelatex` đầu `main.tex`, chỉ cần chạy:
```bash
latexmk main.tex
```
*(Hoặc nhấn Build trong VS Code / TeXstudio)*.

### 2. Chạy thủ công bằng dòng lệnh
```bash
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

### 3. Dùng trên Overleaf
Nén thư mục `template_ctu_qd1799` thành `.zip` -> tải lên Overleaf -> vào **Menu -> Compiler** chọn **XeLaTeX**.
*(Lưu ý: nếu biên dịch trên Linux/Overleaf không có sẵn font `Times New Roman` của Windows, cần tải font `times.ttf`/`timesbd.ttf`/`timesi.ttf`/`timesbi.ttf` vào dự án hoặc đổi `\setmainfont` sang font tương đương như `TeX Gyre Termes`).*
