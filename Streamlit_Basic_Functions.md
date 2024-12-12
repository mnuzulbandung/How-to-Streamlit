## **A. Requirement**

Dalam file app.py utama, masukan script berikut.

```python
import streamlit as st
```

## **B.	Running the Single-Page-Web-App**

Jika Wep App hanya terdiri dari satu laman, untuk menjalankan laman ini, masukkan script berikut pada bagian akhir app.py.

```python
def run():
# Input the page main script here

# Run the app
if __name__ == '__main__':
    run()
```

## **C.	Multi-Page-Web-App**
Dalam Web App, terdapat beberapa laman dengan isi/fungsi khusus. Untuk membuat beberapa laman, diperlukan untuk membuat beberapa file python yang berbeda dari app.py utama. Contoh, file eda.py yang berisi Exploratory Data Analysis dan prediction.py yang berisi model machine learning untuk prediksi.

1.	Untuk menghubungkan file app.py utama dengan eda.py dan prediction.py, masukan script berikut pada app.py sebagai requirement tambahan. Note: Semua file berada di dalam folder bernama deployment.

```python
import deployment.eda as eda
import deployment.prediction as prediction
```

2.	Untuk membuat navigation pane agar bisa menuju dari satu laman ke laman yang lain, masukkan script berikut:

```python
# navigation based on user input
navigation = st.sidebar.selectbox('Choose Page', ('Prediction using Model', 'EDA'))

# page
if navigation == ' Prediction using Model':
    prediction.run()
else:
    eda.run()
```

4.	Untuk menjalankan web app di laman prediction dan eda, masukkan script berikut di bagian akhir eda.py dan prediction.py.

```python
def run():
# Input the page main script here

# Run the app
if __name__ == '__main__':
    run()
```

5.	Dalam app.py tidak perlu memasukkan script poin 4.

## **D. Output Variable**

* Memperlihatkan tulisan sebagai judul

```python
st.title('TITLE')
```

* Memperlihatkan tulisan deskripsi.

```python
st.write('DESCRIPTION')
```

* Membuat garis pemisah.

```python
st.write('---')
```

* Memperlihatkan gambar. Pastikan file gambar berada di lokasi yang sama dengan aplikasi. File gambar bisa diganti dengan link gambar.

```python
st.image('image.png')
```

* Memperlihatkan tabel dataframe.

```python
st.dataframe(df.head())
```

* Memperlihatkan grafik

```python
st.pyplot(fig)
```

## **E. Input Variable**

* Input variable secara manual

```python
user_input = st.text_area('Input your text here:')
```
atau
```python
user_input = st.text_input('Input your text here:', 'Default/Sample Variable')
```

* Input variabel berdasarkan pilihan

```python
option = ['Option_1', ' Option_2']
user_input = st.selectbox('Choose these Options:', option, help = ‘Option_1 is better’)
```
atau
```python
option = ['Option_1', ' Option_2']
user_input = st.radio(' Choose these Options:', option, help = ‘Option_1 is better’)
```

* Input variabel angka. Step merupakan nilai variabel default/sample.

```python
user_input = st.number_input('Input your number here:', step=50)
```

* Input variable untuk mengeksekusi function
```python
if st.button('Press This Button to Execute Function'):
    function_result = function()
    st.write(f'Result: {function_result}')
```
atau
```python
if st.form_submit_button('Press This Button to Execute Function'):
    function_result = function()
    st.write(f'Result: {function_result}')
```
