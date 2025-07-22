Harika! Aşağıdaki içeriği **direkt olarak `documentation.md`** dosyası olarak GitHub’a koyabilirsin.
Tüm UI elementleri, örnekleri ve notları sade ve anlaşılır şekilde yazılmıştır:

---

````markdown
# Dreya UI - Kullanım Rehberi

Bu belge, [`dreya-ui`](https://github.com/dauntIess/dreya-ui) kütüphanesi ile oluşturulan arayüzlerde kullanılabilen tüm UI elementlerini ve örneklerini içerir.

---

## 📦 Kurulum

```lua
local library = loadstring(request({
    Url = "https://raw.githubusercontent.com/dauntIess/dreya-ui/refs/heads/main/library.lua",
    Method = "GET"
}).Body)()
````

---

## 🧱 Temel Yapı

```lua
local Window = library:new({ name = "örnek", sub = ".demo", size = Vector2.new(600, 600) })
local Tab = Window:page({ name = "main", default = true })
local Section = Tab:section({ name = "ayarlar", size = "565" })
```

---

## 🔘 Button (Buton)

```lua
Section:button({
    name = "Bas",
    callback = function()
        print("Butona basıldı.")
    end
})
```

---

## ✅ Toggle (Açma / Kapama)

```lua
Section:toggle({
    name = "Özellik",
    flag = "ozellik_acikmi",
    default = false,
    callback = function(state)
        print("Durum:", state)
    end
})
```

---

## 📝 Textbox (Yazı Kutusu)

```lua
Section:textbox({
    placeholder = "İsim gir",
    flag = "kullanici_ismi",
    default = "",
    callback = function(text)
        print("Yazılan:", text)
    end
})
```

---

## 📥 Dropdown (Açılır Liste)

```lua
Section:dropdown({
    name = "Renk Seç",
    flag = "secili_renk",
    options = { "Kırmızı", "Mavi", "Yeşil" },
    default = "Kırmızı",
    scrollable = true,
    scrollingmax = 4,
    callback = function(value)
        print("Seçilen:", value)
    end
})
```

---

## 🎯 Multibox (Çoklu Seçim)

```lua
Section:multibox({
    name = "Seçenekler",
    flag = "secimler",
    options = { "A", "B", "C", "D" },
    default = { "A" },
    max = 3,
    callback = function(tbl)
        print("Aktif olanlar:", table.concat(tbl, ", "))
    end
})
```

---

## 🎨 ColorPicker (Renk Seçici)

```lua
Section:colorpicker({
    name = "Vurgu Renk",
    flag = "accent_renk",
    default = Color3.fromRGB(255, 100, 100),
    callback = function(color)
        print("Seçilen renk:", color)
    end
})
```

---

## 🎚️ Slider (Kaydırmalı Değer)

```lua
Section:slider({
    name = "Ses",
    flag = "ses_seviyesi",
    min = 0,
    max = 100,
    default = 50,
    suffix = "%",
    float = 1,
    callback = function(value)
        print("Ses:", value)
    end
})
```

---

## 🎮 Keybind (Tuş Atama)

```lua
Section:keybind({
    name = "Menü",
    flag = "menu_toggle",
    default = Enum.KeyCode.M,
    mode = "Toggle", -- "Hold" da olabilir
    callback = function()
        print("Tuşa basıldı.")
    end
})
```

---

## ➖ Divider (Ayırıcı)

```lua
Section:divider({ name = "Ayar Grubu" })
```

---

## 🔔 Notify (Bildirim)

```lua
library:notify({
    title = "Bilgi",
    text = "İşlem başarılı!",
    time = 5
})
```

---

## 📌 Notlar

* Her elementin bir `flag` değeri olmalıdır.
* Tüm `flag`’lara şu şekilde erişebilirsin:

```lua
local deger = library.flags["ozellik_acikmi"]
```

* `scrollable = true` özelliği, dropdown listelerin daha uzun olmasını sağlar.
* Tüm elementler bir `section` içinde tanımlanmalıdır.

---

## 🧪 Örnek: Basit Panel

```lua
local Panel = library:new({ name = "Basit UI", sub = ".test", size = Vector2.new(500, 500) })
local AnaTab = Panel:page({ name = "Tab" })
local Ayarlar = AnaTab:section({ name = "Ayarlar", size = "565" })

Ayarlar:toggle({
    name = "ESP Aç",
    flag = "esp_acik",
    default = true,
    callback = function(b)
        print("ESP:", b)
    end
})
```

---

## ✍️ Ekstra Bilgi

* Kütüphane tam modülerdir.
* UI elementleri birbirini etkileyebilir.
* `library.flags` içinden her değeri dinamik kontrol edebilirsin.

---

## 🔗 Bağlantılar

* UI Kütüphanesi: [github.com/dauntIess/dreya-ui](https://github.com/dauntIess/dreya-ui)
* Kullanım: `request(...)` ile çekilerek loadstring içinde kullanılır.

```

---

İstersen `documentation.md` dosyasını `writefile("documentation.md", [[...]]))` ile script içinde otomatik oluşturan bir kod bloğu da verebilirim. Yardımcı olayım mı?
```
