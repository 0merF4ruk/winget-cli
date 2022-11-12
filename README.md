<h1>Windows Paket Yöneticisi İstemcisi<img src=".github/images/Logo.png" align="left" width="50" height="39"></h1>

Bu depo, Windows Paket Yöneticisi İstemcisi için kaynak kodu içerir.

![winget install wingetcreate](.github/images/WingetInstall.gif)


Windows Paket Yöneticisi'nde yeniyseniz, [Windows Paket Yöneticisi aracını keşfedin](https://docs.microsoft.com/learn/modules/explore-windows-package-manager-tool/?WT.mc_id=AZ-MVP-5004737). İstemcinin kullanabileceği paketler [Windows Paket Yöneticisi Topluluk Deposu](https://github.com/microsoft/winget-pkgs)'nda bulunmaktadır.

## İstemcinin Kurulması

> İstemci şu anda Windows 10 1809 (yapı 17763) veya sonraki bir sürümünü gerektirmektedir. Windows Server 2019, Microsoft Store'da mevcut olmadığından ve güncellenmiş bağımlılıklar bulunmadığından desteklenmemektedir. Windows Server 2022'ye yüklemek mümkün olabilir, bu deneysel olarak kabul edilmelidir (desteklenmemektedir) ve bağımlılıkların da manuel olarak yüklenmesini gerektirir.

### Microsoft Store [Önerilen]

İstemci [Uygulama Yükleyici](https://www.microsoft.com/p/app-installer/9nblggh4nns1) paketi içinde dağıtılır. 

### Geliştirme Sürümleri

Geliştirme sürümlerini almak için iki yöntem vardır:

* Bir [Windows 10 veya Windows 11 Insider](https://insider.windows.com/) derlemesi yükleyin.
* Windows Paket Yöneticisi Insider programına [kaydolarak](http://aka.ms/winget-InsiderProgram) katılın.

Not: Windows Paket Yöneticisi Insider programına katıldığınıza dair e-posta onayı aldıktan sonra güncellenmiş Uygulama Yükleyicisini almanız birkaç gün sürebilir. GitHub'dan en son sürümü yüklemeye karar verirseniz ve Insider programına başarıyla katıldıysanız, bir sonraki geliştirme sürümü Microsoft Store'da yayınlandığında güncellemeler alacaksınız.

Microsoft Store'dan güncellenmiş Uygulama Yükleyicisini aldıktan sonra, deneysel özellikleri görmek için `winget features` komutunu çalıştırabilmeniz gerekir. Bazı kullanıcılar, istemcinin PATH'lerinde bulunmamasıyla ilgili [sorunlar](https://github.com/microsoft/winget-cli/issues/210) bildirmiştir.

### Manuel Olarak Güncelle

Aynı Microsoft Store paketi [Sürümler](https://github.com/microsoft/winget-cli/releases) adresimiz üzerinden de kullanıma sunulacaktır. Bu paketi yüklemenin size WinGet istemcisini vereceğini, ancak Windows Paket Yöneticisi Insider programına katılmadıysanız Microsoft Store'dan otomatik güncellemeleri etkinleştirmeyeceğini unutmayın.

> [VC++ v14 Desktop Framework Package](https://docs.microsoft.com/troubleshoot/cpp/c-runtime-packages-desktop-bridge#how-to-install-and-update-desktop-framework-packages) yüklemeniz gerekebilir.
> Bu yalnızca Windows 10'un eski sürümlerinde ve yalnızca eksik çerçeve paketleriyle ilgili bir hata alırsanız gerekli olmalıdır.

### Sorun Giderme

Lütfen [sorun giderme kılavuzumuzu](/doc/troubleshooting/README.md) okuyun.

## Yöneticinin Dikkat Etmesi Gerekenler

Yükleyici davranışı, yönetici ayrıcalıklarıyla **winget** çalıştırıp çalıştırmadığınıza bağlı olarak farklı olabilir.

* Yönetici ayrıcalıkları olmadan **winget** çalıştırırken, bazı uygulamalar yüklemek için [yükseltme gerektirebilir](https://docs.microsoft.com/windows/security/identity-protection/user-account-control/how-user-account-control-works). Yükleyici çalıştığında, Windows sizden [yükseltme](https://docs.microsoft.com/windows/security/identity-protection/user-account-control/how-user-account-control-works#the-uac-user-experience) yapmanızı isteyecektir. Yükseltmemeyi seçerseniz, uygulama yüklenemeyecektir.  

* Bir Yönetici Komut İsteminde **winget** çalıştırırken, uygulama gerektiriyorsa [yükseltme istemlerini](https://docs.microsoft.com/windows/security/identity-protection/user-account-control/how-user-account-control-works#the-uac-user-experience) görmezsiniz. Komut isteminizi yönetici olarak çalıştırırken her zaman dikkatli olun ve yalnızca güvendiğiniz uygulamaları yükleyin.

### Kendiniz inşa edin

Ayrıca [istemciyi kendiniz de oluşturabilirsiniz](#building-the-client). İstemci tamamen işlevsel olsa da, henüz resmi dağıtım mekanizmalarının dışında çalışan istemciler için tam destek sağlamaya hazır değiliz. Bir Sorun açmaktan çekinmeyin, ancak daha düşük öncelik alabileceğini bilin.

## Yapı Durumu

[![Yapı Durumu](https://dev.azure.com/ms/winget-cli/_apis/build/status/microsoft.winget-cli?branchName=master)](https://dev.azure.com/ms/winget-cli/_build/latest?definitionId=344&branchName=master)

## Windows Paket Yöneticisi Sürüm Yol Haritası
Bir sonraki Windows Paket Yöneticisi sürümlerini sunma planı [tartışmalar](https://github.com/microsoft/winget-cli/discussions/2063) adresinde açıklanmıştır ve proje ilerledikçe güncellenecektir.

## Windows Paket Yöneticisine Genel Bakış
Windows Paket Yöneticisi**, bilgisayar ortamınızı özel kılan paketleri hızlı ve kolay bir şekilde keşfetmenize ve yüklemenize yardımcı olmak için tasarlanmış bir araçtır.  Windows Paket Yöneticisini** kullanarak, tek bir komutla favori paketlerinizi yükleyebilirsiniz:

`winget install <package>`

## Genel Bakış  

### Müşteri Deposu
Bu winget-cli deposu, istemciyi oluşturmak için tasarlanmış kaynak kodunu içerir.  Bu istemcinin geliştirilmesine katılmanız teşvik edilmektedir.[Issues](https://github.com/microsoft/winget-cli/issues) adresimizde çok sayıda birikmiş özelliğimiz var. İstediklerinizi onaylayabilir, daha fazlasını ekleyebilir ve hatta [bir tanesine başlayabilirsiniz](https://github.com/microsoft/winget-cli/projects/1)

### Kaynaklar
İstemci, kaynaklar kavramı etrafında inşa edilmiştir; etkin bir şekilde bir dizi paket. Kaynaklar, istemcinin üzerinde işlem yapabilmesi için paketler hakkındaki meta verileri keşfetme ve alma yeteneği sağlar.

* Varsayılan "winget" kaynağı [Windows Paket Yöneticisi Topluluk Deposu](https://github.com/microsoft/winget-pkgs) içindeki paketleri içerir.
* Varsayılan "msstore" kaynağı Microsoft Store'daki paketleri içerir.
* Kendi özel [REST tabanlı](https://github.com/microsoft/winget-cli-restsource) kaynağınızı barındırmanız da mümkündür.

## Müşteri oluşturma

### Ön Koşullar

* Windows 10 1809 (17763) veya üstü
* [Geliştirici Modu etkin](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
* [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/)
   * Ya da yüklemek için winget kullanın ;) (Araçlar->Araçları ve Özellikleri Al... aracılığıyla iş yüklerini ayarlamanız gerekebilir)
* Aşağıdaki iş yükleri:
   * .NET Masaüstü Geliştirme
   * C++ ile Masaüstü Geliştirme
   * Evrensel Windows Platformu Geliştirme
* Aşağıdaki uzantılar:
   * [Microsoft Visual Studio Installer Projeleri](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2022InstallerProjects)

### Yapı

Şu anda yalnızca çözümü kullanarak derleme yapıyoruz; bir VS çözümü oluşturmanın komut satırı yöntemleri de çalışmalıdır.

## Kredi

Keivan Beigi'ye (@kayone)](https://github.com/kayone) Windows Paket Yöneticisi için ilk proje yöneliminde bize yardımcı olan AppGet üzerindeki çalışmaları için teşekkür ederiz.

## Katkıda Bulunan

Bu proje katkı ve önerileri memnuniyetle karşılamaktadır.  Çoğu katkı, aşağıdakileri kabul etmenizi gerektirir
Katkıda Bulunan Lisans Sözleşmesi (CLA), bize aşağıdakileri verme hakkına sahip olduğunuzu ve gerçekten de verdiğinizi beyan eder
katkınızı kullanma hakkına sahiptir. Ayrıntılar için https://cla.opensource.microsoft.com adresini ziyaret edin. Daha fazla 
bilgiler [CONTRIBUTING.md](/CONTRIBUTING.md) dosyamızda mevcuttur.

Bir çekme isteği gönderdiğinizde, bir CLA botu aşağıdakileri sağlamanız gerekip gerekmediğini otomatik olarak belirleyecektir
a CLA ve PR'yi uygun şekilde süsleyin (örn. durum kontrolü, yorum). Talimatları takip etmeniz yeterlidir
bot tarafından sağlanır. Bunu CLA'mızı kullanarak tüm depolarda yalnızca bir kez yapmanız gerekecektir.

Bu proje [Microsoft Açık Kaynak Davranış Kuralları](https://opensource.microsoft.com/codeofconduct/)'nı benimsemiştir.
Daha fazla bilgi için lütfen [Davranış Kuralları SSS](https://opensource.microsoft.com/codeofconduct/faq/) veya
Ek sorularınız veya yorumlarınız için [opencode@microsoft.com](mailto:opencode@microsoft.com) ile iletişime geçin.

## Veri/Telemetri

winget.exe istemcisi, kullanım ve tanılama (hata) verilerini toplamak ve ürünü geliştirmeye yardımcı olması için Microsoft'a göndermek üzere enstrümante edilmiştir. 

İstemciyi kendiniz oluşturursanız, enstrümantasyon etkinleştirilmez ve Microsoft'a hiçbir veri gönderilmez.

winget.exe istemcisi makine genelindeki gizlilik ayarlarına saygı duyar ve kullanıcılar Microsoft Windows gizlilik bildiriminde [burada](https://support.microsoft.com/help/4468236/diagnostics-feedback-and-privacy-in-windows-10-microsoft-privacy) belgelendiği gibi cihazlarında devre dışı bırakabilirler. Buna ek olarak, [settings](https://docs.microsoft.com/windows/package-manager/winget/settings) kullanarak telemetriyi açıkça engelleyebilirsiniz.

Kısacası, devre dışı bırakmak için `Başlat`a gidin, ardından `Ayarlar` > `Gizlilik` > `Teşhis ve geri bildirim` öğelerini seçin ve `Temel` öğesini seçin. 

Daha fazla ayrıntı için [gizlilik beyanına] (privacy.md) bakın.
