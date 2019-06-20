package responsi2;

import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;
//**KODE BOOKING DIAMBIL DARI NAMA/PEMBERANGKATAN /TUJUAN/JUMLAH TIKET
//funtion,MENU, menu pembatalan,           

class Tanggal {

    static String getTanggal;
    Date date = new Date();

    void getTanggal() {
        SimpleDateFormat ft = new SimpleDateFormat("dd/MM/yy");
        System.out.println(ft.format(date));
        System.out.println("");
    }

    void getWaktu() {
        SimpleDateFormat ft = new SimpleDateFormat("hh:mm:ss a");
        System.out.println(ft.format(date));
        System.out.println("");
    }
}

public class Responsi2 {

    public static void main(String[] args) {
        menu_awal();
    }
    static Scanner sc = new Scanner(System.in);

    static char ulang;

    public static void menu_awal() {
        int pilih_menu;
        ulang = 'S';
        do {
            System.out.println("========== MENU TIKET MURAH ==========");
            System.out.println("1.\tList Penerbangan");
            System.out.println("2.\tTransaksi");
            System.out.println("=====================================");
            System.out.print("Pilih : ");

            pilih_menu = sc.nextInt();

            System.out.println("");
            switch (pilih_menu) {
                case 1:
                    list();
                    break;

                case 2:
                    transaksi();
                    break;

                default:
                    System.out.println("Inputan salah!");
            }
            System.out.print("ingin kembali ke menu awal ?(Y/T) ");
            ulang = sc.next().charAt(0);
        } while (ulang == 'Y' || ulang == 'y');
    }

    public static void list() {

        System.out.println("=========================================");
        System.out.println("Detail Tiket Tersedia-Harga Pesawat Murah");
        System.out.println();
        System.out.println("=========================================");
        System.out.println("     1.TOKYO        Rp.3400000           ");
        System.out.println("     berangkatan    JAKARTA/08:00        ");
        System.out.println("     Tiba           TOKYO/14:20          ");
        System.out.println("     2.HARUJUKU     Rp.2000000           ");
        System.out.println("     berangkatan    JAKARTA/09:00        ");
        System.out.println("     Tiba           HARUKUKU/15:00       ");
        System.out.println("     3.KYOTO        Rp.5400000    ");
        System.out.println("     berangkatan    SURABAYA/12:00       ");
        System.out.println("     Tiba           KYOTO/17:30          ");
        System.out.println("     4.OSAKA      Rp.4300000    ");
        System.out.println("     5.SAPPORO    Rp.1700000    ");
        System.out.println("=========================================");
    }

    public static void transaksi() {
        Tanggal tgl = new Tanggal();
        Scanner userinput = new Scanner(System.in);
        Calendar call = new GregorianCalendar();
        int pesanan = 0;
        int jumlah = 0, bayar, tagihan = 0, pajak, kembali;
        int bulan, tahun, hari, jam, menit, detik;
        System.out.println("------------------------SELAMAT DATANG DI TIKET MURAH--------------------------");
        System.out.println("===============================================================================");
        System.out.print("Masukan Jumlah Pesanan : ");
        pesanan = userinput.nextInt();

        int[] tiket = new int[pesanan];
        int[] tujuan = new int[pesanan];
        String infotujuan = null, infoakhir = null;
        String[] namatujuan = new String[pesanan];
        System.out.print("Masukan Nama Anda : ");
        String nama = userinput.next();
        System.out.println();
        System.out.println("==========================================");
        System.out.println("-----Detail Tiket Penerbangan Jakarta-----");
        System.out.println();
        System.out.println("==========================================");
        System.out.println("     1.TOKYO        Rp.3400000           ");
        System.out.println("     berangkatan    JAKARTA/08:00        ");
        System.out.println("     Tiba           TOKYO/14:20          ");
        System.out.println("     2.HARUJUKU     Rp.2000000           ");
        System.out.println("     berangkatan    JAKARTA/09:00        ");
        System.out.println("     Tiba           HARUKUKU/15:00       ");
        System.out.println("     3.KYOTO        Rp.5400000    ");
        System.out.println("     berangkatan    JAKARTA/12:00       ");
        System.out.println("     Tiba           KYOTO/17:30          ");
        System.out.println("     4.OSAKA      Rp.4300000    ");
        System.out.println("     berangkatan    JAKARTA/22:00       ");
        System.out.println("     Tiba           OSAKA/07:30          ");
        System.out.println("     5.SAPPORO    Rp.1700000    ");
        System.out.println("     berangkatan    JAKARTA/16:50       ");
        System.out.println("     Tiba           SAPPORO/23:40          ");
        System.out.println("==========================================");
        System.out.println();
        for (int i = 0; i < pesanan; i++) {
            System.out.print("Masukan No tujuan = ");
            tujuan[i] = userinput.nextInt();
            System.out.print("Masukan Jumlah Tiket = ");
            jumlah = userinput.nextInt();

            if (tujuan[i] == 1) {
                namatujuan[i] = "TOKYO";
                tiket[i] = 3400000;
                infotujuan = "JAKARTA/08:00";
                infoakhir = "TOKYO/14:20";
            } else if (tujuan[i] == 2) {
                namatujuan[i] = "HARUJUKU";
                tiket[i] = 2000000;
                infotujuan = "JAKARTA/09:00";
                infoakhir = "HARUJUKU/15:00";
            } else if (tujuan[i] == 3) {
                namatujuan[i] = "KYOTO";
                tiket[i] = 5400000;
                infotujuan = "JAKARTA/12:00";
                infoakhir = "KYOTO/17:30";
            } else if (tujuan[i] == 4) {
                namatujuan[i] = "OSAKA";
                tiket[i] = 4300000;
                infotujuan = "JAKARTA/16:00";
                infoakhir = "OSAKA/22:00";
            } else if (tujuan[i] == 5) {
                namatujuan[i] = "SAPPORO";
                tiket[i] = 1700000;
                infotujuan = "JAKARTA/16:50";
                infoakhir = "SAPPORO/23:40";
            } else {
                System.out.println("Tujuan Tidak Temukan Coba Ulang Pemesanan");
            }
            pajak = tiket[i] * 10 / 100;
            if (tiket[i] > 3) {
                tiket[i] = tiket[i] * 2 / 100;
            }
//tanggal disini
            tagihan = (tiket[i] * jumlah) + pajak;
            System.out.println("Membeli Dengan Jumlah " + jumlah + " tiket pesawat dengan tujuan " + namatujuan[i]);
            System.out.println("Tagihan anda adalah sebesar Rp. " + tagihan);
            System.out.println("Sudah termasuk PAJAK 10%");
            System.out.print("Jumlah yang Dibayar : Rp.");
            bayar = userinput.nextInt();
            System.out.println();

            System.out.println("===============================================================================");
            System.out.println();
            kembali = bayar - tagihan;
            while (bayar < tagihan) {
                System.out.println("Uang Anda Kurang");
                System.out.print("Masukan Uang = RP.");
                int tambahan = userinput.nextInt();
                bayar = bayar + tambahan;
            }

            System.out.println("Kembalian Anda Sebesar Rp. " + kembali);
            System.out.println("");
            System.out.println("===============================================================================");

        }
        for (int a = 0; a < pesanan; a++) {
            System.out.println("---------TERIMAKASIH TELAH MEMPERCAYAI KAMI----------");
            System.out.println("Nama Pemesan           :" + nama);
            System.out.println("Tujuan Anda            :" + namatujuan[a]);
            System.out.println("Jadwal Pemberangkatan  :" + infotujuan);
            System.out.println("Jadwal Sampai Tujuan   :" + infoakhir);
            System.out.print("Tanggal Pemesanan Anda :");
            tgl.getTanggal();
            System.out.print("Waktu Pemesanan Anda   :");
            tgl.getWaktu();
            System.out.println("Jumlah yang Anda Beli  :" + jumlah);
            System.out.println("Total Harga            :" + tagihan);
            System.out.println("------------TIKET MURAH PALING OKE-------------------");
        }
    }

}
