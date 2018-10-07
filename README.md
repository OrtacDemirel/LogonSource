Programı kullanmadan önce aşağıdaki yazıyı dikkatlice okumanızı öneririm.

Domain ortamında herhangi bir kaynak üzerinden oturum açma ve yetkilendirme işlemleri Kerberos tarafından yapılır. Domain controller makineler bu işlemleri varsayılan olarak detaylı olarak kayıt altına almaz. Bu yüzden programın sonuç döndürmesi için öncelikle “Default domain Controller Policy” üzerinden oturum açma işlemlerinin kayıt altına alınması ayarı yapılmalıdır.

Güvenlik ayarlarında yer alan “Advanced audit Policy configuration” bölümünden Aduit Policies > Logon/Logoff bölümüne gelin ve “Audit Logon”   politikasını “success” olarak ayarlayın.

Sadece DC ler üzerinde yapılan bu değişiklik ile artık tüm Kerberos işlemleri detaylı bir şekilde kayıt altına alınacaktır. Olay günlüklerinde güvenlik bölümüne 4624 id ile kayıtlar düşmektedir.

NOT: Bu ayardan sonra çok fazla kayıt olay görüntüleyicisine yazılır.  Bunun sebebi de aynı kaynak üzerinden gelen Kerberos kayıtlarının birden fazla olmasıdır.  Logon ID, Logon GUID ve Source Port çok fazla olabilir. DC ler üzerinde artan olay kayıtları sizin için sıkıntı olacak ise bu ayarı yapmayınız. Bu durumda programda çalışmaz.

Kısa süre önce oturum açan hesabı bulma ile uzun süre önce oturum açan hesabı bulma arasında arama işlemi çok uzun sürebileceğinden dolayı arama yapılacak kayıt sayısını girmeniz gerekmektedir. Bu sayı en son kayıt edilen kaç adet olay günlüğüne bakılacağıdır.

Çalışması için .net 4.5.1 ve en az powershell 3.0 gereklidir.

.net 4.5.1 :
https://www.microsoft.com/tr-tr/download/confirmation.aspx?id=40779
Powershell 3.0:
https://www.microsoft.com/en-us/download/confirmation.aspx?id=34595
