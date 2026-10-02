# dashboard-perpustakaan
Mini dashboard perpustakaan full-stack (Vue 3 + FastAPI) - Rodina Fitriani 25120300007
Dashboard Perpustakaan (Soal A — NIM Ganjil)
Nama: Rodina Fitriani NIM: 25120300007

Mini dashboard full-stack: Vue 3 (Composition API, Vue Router) + FastAPI (Pydantic, OpenAPI). Entitas Buku: id, judul, penulis, kategori, stok.

Fitur
Pencarian berdasarkan judul atau penulis
Urutan A-Z / Z-A berdasarkan judul
Badge status stok: Tersedia, Menipis, Stok Habis
4 tile ringkasan (computed): Total Buku, Stok Menipis + Habis, Jumlah Kategori, Total Eksemplar
Tambah, ubah, dan hapus buku (CRUD)
21 data seed buatan sendiri (backend/app/data.py)
Ambang status stok
Stok	Status
0	Stok Habis
1 – 5	Menipis
> 5	Tersedia
Alasan: perpustakaan umumnya menyediakan beberapa eksemplar per judul, sehingga ≤ 5 dianggap perlu segera ditambah. Konstanta BATAS_MENIPIS ada di frontend/src/composables/useBooks.js.

Menjalankan
Backend (port 8000)

cd backend
python -m venv venv && source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload

Dokumen OpenAPI: http://localhost:8000/docs

Frontend (port 5173)

cd frontend
npm install
npm run dev

Kontrak REST
Method	Endpoint	Keterangan
GET	/api/books?q=&sort=asc|desc	Daftar buku
GET	/api/books/{id}	Detail buku
POST	/api/books	Tambah (201)
PUT	/api/books/{id}	Ubah
DELETE	/api/books/{id}	Hapus (204)
Struktur
backend/app: main.py, routers_books.py, schemas.py (Pydantic), data.py
frontend/src: api.js (fetch async), composables/useBooks.js, views/, App.vue, main.js (router)
