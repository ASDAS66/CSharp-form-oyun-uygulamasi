# CSharp-form-oyun-uygulamasi
C# form ile Ödev olarak yaptığım uygulama; kullanıcı girişi, kayıt yenileme ekranı ve işlem yapma ile ilgili bir oyunu içermektedir. Projemde olabildiğince çok tools kullanımına ve kodlarına yer vermeye çalıştım.
## 1.Form1
Form1 uygulamsında, kullanıcı girişi ve kullanıcı kaydı yapılmaktadır. CodeFirst ile yaptığım uygulamada kullanıcı giriş yapmak için bu ekran kullnılmaktadır. Kyıtlı olan kullanıcı kullanıcı adını ve şifresini girmelidir. Şifre için eklenen textboxta şifre güvenliği için şifre karekterleri yerine * ekler.
textboxların boş geçilmemesi için MessageBox eklenmiştir. boş geçilirse uyarı vermektedir.
Kullanıcı giriş yaptığında bilgileri sorgulanır ve form2 ye geçiş yapar. form ikiye geçmek için kullanılan kod aşağıdaki gibidir.

“`
if (dr.Read())
{
    Form2 frm = new Form2();
    frm.ShowDialog();
    //kullanici ve sifre doğruysa form2'ye geçer(giriş yapılır)
 }
“`

## 2.Form2
uygulamanın form2 kısmında ise oyun başlamaktadır. kullanıcı bilgilerini doğru girerse bu ekrana gelmektedir. Burada işlem Oyun zorluk derecelerine göre işlem yeteneği sınanmaktadır. Kolay, Orta, Zor seçenekleri mevcuttur. Kolay seçeneğinde 0-50 arası, orta seçeneğinde 50-200 arası, zor seçeneğinde ise 200-1000 arası sayılarla işlem yapoşmaktadır. ve bütün bunları yapmak için belirli bir süre verilmiştir.
#### FORM ARKA PLAN RENGİ DEĞİŞTİRME:
“`
this.BackColor = Color.SteelBlue;
this.Text = "**Sayıyı Bul**";
//form1 arka plan rengini düzenler
“`
#### lABELİN FONTUNU VE TEXTİNİ DÜZENLEME
“`
label4.Font = new Font("Georgia", 12, FontStyle.Italic);
label4.Text = "=";
“`
#### BUTON AYARLARI
“`
button2.Text = "cevapla";
button2.Font = new Font("Georgia", 8, FontStyle.Bold);
button2.Enabled = false;
“`
#### LİSTBOX KULLANIMI
“`
listBox1.BackColor = Color.MediumPurple;
  listBox1.Items.Add("mor");
  listBox1.Items.Add("yeşil");
  listBox1.Items.Add("pembe");
  listBox1.Items.Add("sarı");
//listbox un arka plan rengini belirler ve indexlerini ekler.
“`
#### RASTGELE SAYI ÜRETME
“`
 if (radioButton1.Checked == true)
{              
  sayi1 = rastgele.Next(0, 51);
  sayi2 = rastgele.Next(0, 51);
  //radiobutton1 seçildiğinde 1 ile 50 arasında rastgele sayı uretir.
  label1.Text = sayi1.ToString();
  label2.Text = sayi1.ToString();
  //üretilen sayılar labellere yazılır.
}
“`
#### OYUNDA TİMER KULLANIMI
“`
 private void timer1_Tick(object sender, EventArgs e)
{
  süre--;
  label9.Text = süre.ToString();
    //süreyi 1 er 1er azaltır ve label9 a yazdırır.
    progressBar1.Value += 1;
    progressBar1.Minimum = 0;
    progressBar1.Maximum = 60;
    progressBar1.Step = 5;
    //progressaBarın min/max değerlerini belirler ve progressBarı 1er 1er arttırır.
             if (süre == 0)
            {
              button1.Enabled = false;
              button2.Enabled = false;
              timer1.Stop();
              süre = 60;
              button3.Visible = true;
              //süre 0 olduğunda button1 ve button2 erişilmez olur timer durur.
            }
             }
“`
## 3-Form3
Bur forma, form1 ekranındaki kayıtol butonuna tıklayarak gelinmektedir. burada kullanıcı bilgileri alınarak kullanıcı veritabanına kayıt edilmektedir. Ve ayrıca kullanıcı hem kendi kaydını hem de oyundaki diğer kullanıcıları görmek adına kayıt görüntüle ekranından kullanıcıları görüntüleyebilir.
#### KAYIT EKLEME
“`
public void kayıtekle()
        {
            if (textBox1.Text!=null && textBox2.Text != null)
            {
                Conn.Open();
                string kayit = "insert into oyuncular (kAdı,sifre,dTarihi,yaş,cinsiyet) values (@ku,@sf,@dt,@ys,@cns)";
                SqlCommand komut = new SqlCommand(kayit, Conn);
                komut.Parameters.AddWithValue("@ku", textBox1.Text);
                komut.Parameters.AddWithValue("@sf", textBox2.Text);
                komut.Parameters.AddWithValue("@dt", dateTimePicker1.Text);
                komut.Parameters.AddWithValue("@ys", numericUpDown1.Value);
                komut.Parameters.AddWithValue("@cns", comboBox1.Text);
                komut.ExecuteNonQuery();
                Conn.Close();                           
            }
            kayıtgörüntüle();
            //yeni kayıt ekleme işlemi yapar.
        }
“`
#### KAYIT GÖRÜNTÜLEME
“`
 public void kayıtgörüntüle()
        {
            Conn.Open();
            string kayıt = "select*from oyuncular";
            SqlCommand komut = new SqlCommand(kayıt, Conn);
            SqlDataAdapter da = new SqlDataAdapter(komut);
            DataTable dt = new DataTable();
            da.Fill(dt);
            dataGridView1.DataSource = dt;
            Conn.Close();
            //oyuncular tablosundan verileri datagridviewe gösterir.
        }
“`

#### KAYIT SİLME
“`
void KayıtSil(int kAdı)
        {
            string sql = "DELETE FROM oyuncular WHERE kAdı=@ka";
            SqlCommand komut = new SqlCommand(sql, Conn);
            komut.Parameters.AddWithValue("@ka",kAdı);
            Conn.Open();
            komut.ExecuteNonQuery();
            Conn.Close();
            //oyuncular tablosundan kullanıcı adına göre kayıt siler.
        }
“`

           


