# c-3

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Data.SqlClient;


//Data Source=NTB1000088;Initial Catalog=TestYolcuBilet;User ID=sa;Password=sa321sa?

namespace TestSeferSeyahat
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        SqlConnection baglanti=new SqlConnection(@"Data Source=NTB1000088;Initial Catalog=TestYolcuBilet;User ID=sa;Password=sa321sa?");

        void seferlistesi()
        {
            SqlDataAdapter da=new SqlDataAdapter("Select * from TblSeferBilgi",baglanti);
            DataTable dt = new DataTable();
            da.Fill(dt);
            dataGridView1.DataSource = dt;

        }

        private void button3_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "3";
        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void maskedTextBox3_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)
        {

        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void label8_Click(object sender, EventArgs e)
        {

        }

        private void label9_Click(object sender, EventArgs e)
        {

        }

        private void groupBox4_Enter(object sender, EventArgs e)
        {

        }

        private void label19_Click(object sender, EventArgs e)
        {

        }

        private void btnKaydet_Click(object sender, EventArgs e)
        {
            baglanti.Open();
            SqlCommand komut = new SqlCommand("insert into TblYolcuBilgi (Ad,Soyad,Tc,Cinsiyet,Telefon,Mail) values (@p1,@p2,@p3,@p4,@p5,@p6)",baglanti);
            komut.Parameters.AddWithValue("@p1", txtAd.Text);
            komut.Parameters.AddWithValue("@p2",mskSoyad.Text);
            komut.Parameters.AddWithValue("@p3", mskTc.Text);
            komut.Parameters.AddWithValue("@p4", cmbCinsiyet.Text);
            komut.Parameters.AddWithValue("@p5", mskTelefon.Text);
            komut.Parameters.AddWithValue("@p6",mskMail.Text);
            komut.ExecuteNonQuery();
            baglanti.Close();
            MessageBox.Show("Yolcu bilgisi sisteme kaydedildi.","Bigi", MessageBoxButtons.OK, MessageBoxIcon.Information);
        }

        private void btnSeferOlustur_Click(object sender, EventArgs e)
        {
            baglanti.Open();
            SqlCommand komut = new SqlCommand("insert into TblSeferBilgi (Kalkis,Varis,Tarih,Saat,Kaptan,Fiyat) values (@p1,@p2,@p3,@p4,@p5,@p6)", baglanti);
            komut.Parameters.AddWithValue("@p1",txtKalkis.Text);
            komut.Parameters.AddWithValue("@p2",txtVaris.Text);
            komut.Parameters.AddWithValue("@p3",mskTarih.Text);
            komut.Parameters.AddWithValue("@p4",mskSaat.Text);
            komut.Parameters.AddWithValue("@p5",mskKaptan.Text);
            komut.Parameters.AddWithValue("@p6",txtFiyat.Text);
            komut.ExecuteNonQuery();
            baglanti.Close();
            MessageBox.Show("Sefer bilgisi sisteme kaydedildi","Bilgi", MessageBoxButtons.OK,MessageBoxIcon.Information);
            seferlistesi();
        }
        

        private void btnKaptan_Click(object sender, EventArgs e)
        {
            baglanti.Open();
            SqlCommand komut = new SqlCommand("insert into TblKaptan (KaptanNo,AdSoyad,Telefon) values (@p1,@p2,@p3)", baglanti);
            komut.Parameters.AddWithValue("@p1",txtKaptanNo.Text);
            komut.Parameters.AddWithValue("@p2",txtAdSoyad.Text);
            komut.Parameters.AddWithValue("@p3",mskKaptanTelefon.Text);
            komut.ExecuteNonQuery();
            baglanti.Close();
            MessageBox.Show("Kaptan bilgisi sisteme kaydedildi","Bilgi",MessageBoxButtons.OK,MessageBoxIcon.Warning);


        }

        private void Form1_Load(object sender, EventArgs e)
        {
            seferlistesi();

        }

        private void dataGridView1_CellClick(object sender, DataGridViewCellEventArgs e)
        {
            int secilen= dataGridView1.SelectedCells[0].RowIndex;
            txtSeferNumara.Text = dataGridView1.SelectedRows[secilen].Cells[0].Value.ToString();
        }

        private void btn1_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "1";
        }

        private void btn2_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "2";
        }

        private void btn4_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "4";
        }

        private void btn5_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "5";
        }

        private void btn6_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "6";
        }

        private void btn7_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "7";
        }

        private void btn8_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "8";
        }

        private void btn9_Click(object sender, EventArgs e)
        {
            txtKoltukNo.Text = "9";
        }
    }
}
