# CSharp-form-oyun-uygulamasi
C# form ile Ödev olarak yaptığım uygulama; kullanıcı girişi, kayıt yenileme ekranı ve işlem yapma ile ilgili bir oyunu içermektedir. Projemde olabildiğince çok tools kullanımına ve kodlarına yer vermeye çalıştım.
## 1-Form1
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
## 2-Form2
            
