# Qwen Code Türkçe — MCP Rehberi

Bu bölüm, Qwen Code'un Model Context Protocol (MCP) desteğinin Türkçe kullanım rehberidir.

> [!IMPORTANT]
> Bu depo Qwen ekibinin resmi projesi değildir. Bağımsız Türkçe topluluk dokümantasyonudur.

## MCP Nedir?

MCP (Model Context Protocol), yapay zekâ uygulamalarının harici araçlara ve veri kaynaklarına standart bir yöntemle bağlanmasını sağlayan bir protokoldür.

Qwen Code, MCP sunucuları üzerinden yeteneklerini genişletebilir.

MCP sayesinde Qwen Code uygun araçlar sağlandığında:

- dosya sistemleriyle çalışabilir,
- repository araçlarına bağlanabilir,
- API servislerini kullanabilir,
- veritabanlarıyla iletişim kurabilir,
- özel geliştirme araçlarını çağırabilir,
- otomasyon sistemlerini kullanabilir,
- harici servislerden veri alabilir.

MCP sunucusu burada Qwen Code ile harici sistem arasında bir köprü görevi görür.

---

# 1. Qwen Code MCP Yapısı

Qwen Code MCP sunucularını yapılandırma dosyasındaki `mcpServers` bölümünden yükleyebilir.

Genellikle iki yapılandırma kapsamı kullanılır.

Kullanıcı kapsamı:

```text
~/.qwen/settings.json
