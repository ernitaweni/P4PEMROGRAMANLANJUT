# P4PEMROGRAMANLANJUT
class persegiPanjang
{
public:
    int x_min;
    int y_min;
    int x_max;
    int y_max;

    persegiPanjang(int _x_min, int _x_max, int _y_min, int _y_max)
    {
        x_min = _x_min;
        y_min = _y_min;
        x_max = _x_max;
        y_max = _y_max;
    }
Kode diatas mendefinisikan kelas persegiPanjang. Kelas ini memiliki empat variabel anggota (x_min, y_min, x_max, y_max) yang merepresentasikan koordinat persegi panjang. Constructor persegiPanjang digunakan untuk menginisialisasi objek persegiPanjang dengan memberikan nilai awal untuk koordinatnya.

    bool operator==(const persegiPanjang &p)
    {
        if (x_min < p.x_max && x_max > p.x_min && y_min < p.y_max && y_max > p.y_min)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
Fungsi diatas membandingkan dua objek persegiPanjang dan mengembalikan true jika mereka saling tumpang tindih (overlap), dan false jika tidak.

    persegiPanjang operator+(const persegiPanjang &p)
    {
        int x_min_new = min(x_min, p.x_min);
        int y_min_new = min(y_min, p.y_min);
        int x_max_new = max(x_max, p.x_max);
        int y_max_new = max(y_max, p.y_max);

        return persegiPanjang(x_min_new, x_max_new, y_min_new, y_max_new);
    }
Fungsi diatas menghitung persegi panjang baru yang merupakan hasil dari penggabungan (union) dua persegi panjang yang diberikan.

    persegiPanjang operator-(const persegiPanjang &p)
    {
        int x_min_new = max(x_min, p.x_min);
        int y_min_new = max(y_min, p.y_min);
        int x_max_new = min(x_max, p.x_max);
        int y_max_new = min(y_max, p.y_max);

        return persegiPanjang(x_min_new, x_max_new, y_min_new, y_max_new);
    }
Fungsi diatas menghitung persegi panjang baru yang merupakan hasil dari pengurangan (difference) dua persegi panjang yang diberikan.

    persegiPanjang &operator++()
    {
        x_max *= 2;
        y_max *= 2;

        return *this;
    }
Fungsi diatas menggandakan panjang dan lebar persegi panjang.

    void display()
    {
        cout << "x_min: " << x_min << endl;
        cout << "y_min: " << y_min << endl;
        cout << "x_max: " << x_max << endl;
        cout << "y_max: " << y_max << endl;
    }
};

Method display digunakan untuk mencetak koordinat persegi panjang.

int main()
{
    persegiPanjang a(2, 5, 4, 8);
    persegiPanjang b(4, 7, 1, 8);

    persegiPanjang c = a + b;
    persegiPanjang d = a - b;

    persegiPanjang e = ++a;

    cout << (a == b ? "true" : "false") << endl;

    cout << "----------- +" << endl;
    c.display();
    cout << "----------- -" << endl;
    d.display();
    cout << "----------- ++" << endl;
    e.display();

    return 0;
}

Kode diatas adalah fungsi utama (main). Di dalamnya, objek-objek persegiPanjang dibuat, operasi-operasi dilakukan, dan hasilnya dicetak ke layar dengan  membuat objek yaitu a dan b dan menggunakan method display().


Kode di atas mendefinisikan sebuah kelas persegiPanjang yang merepresentasikan persegi panjang melalui koordinat sudut kiri bawah (x_min, y_min) dan sudut kanan atas (x_max, y_max). Kelas ini memiliki beberapa operator overloading untuk melakukan operasi aritmatika dan perbandingan antara objek-objek persegi panjang. 
