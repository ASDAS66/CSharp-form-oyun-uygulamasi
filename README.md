# CSharp-form-oyun-uygulamasi
C# form ile Ödev olarak yaptığım uygulama; kullanıcı girişi, kayıt yenileme ekranı ve işlem yapma ile ilgili bir oyunu içermektedir. Projemde olabildiğince çok tools kullanımına ve kodlarına yer vermeye çalıştım.
## 1.Form1
Form1 uygulamsında, kullanıcı girişi yapılmaktadır. CodeFirst ile yaptığım uygulamada kullanıcı giriş yapmak için bu ekran kullnılmaktadır. Kyıtlı olan kullanıcı kullanıcı adını ve şifresini girmelidir. Şifre için eklenen textboxta şifre güvenliği için şifre karekterleri yerine * ekler.
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
uygulamanın form2 kısmında ise oyun başlamaktadır. kullanıcı bilgilerini doğru girerse bu ekrana gelmektedir.
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
            
