Anladım şimdi — senin istediğin şey şu:

**"dreya-ui'de nasıl `button`, `toggle`, `textbox`, `dropdown`, `colorpicker`, `slider`, `keybind` gibi UI elementleri yapılır?"**

Yani aslında bir **element rehberi** istiyorsun.

Aşağıya **tek mesajda**, sade ve örnekli şekilde her şeyi yazıyorum. Bu, `documentation.md` içine koyulabilir:

---

````markdown
# Dreya UI - Element Kullanım Rehberi

Bu belge, `dreya-ui` sisteminde kullanılabilen tüm UI elementlerinin nasıl oluşturulduğunu gösterir.

---

## 🧱 Temel Yapı

```lua
local Window = library:new({ name = "örnek", sub = ".demo", size = Vector2.new(600, 600) })
local Tab = Window:page({ name = "main", default = true })
local Section = Tab:section({ name = "ayarlar", size = "565" })
````

---

## 🔘 Button (Buton)

```lua
Section:button({
    name = "bas",
    callback = function()
        print("butona basıldı")
    end
})
```

---

## ✅ Toggle (Açma/Kapama)

```lua
Section:toggle({
    name = "özellik",
    flag = "ozellik_acikmi",
    default = false,
    callback = function(state)
        print("durum:", state)
    end
})
```

---

## 📝 Textbox (Yazı Kutusu)

```lua
Section:textbox({
    placeholder = "isim gir",
    flag = "kullanici_ismi",
    default = "",
    callback = function(text)
        print("yazılan:", text)
    end
})
```

---

## 📥 Dropdown (Açılır Liste)

```lua
Section:dropdown({
    name = "renk seç",
    flag = "secili_renk",
    options = { "Kırmızı", "Mavi", "Yeşil" },
    default = "Kırmızı",
    scrollable = true,
    scrollingmax = 4,
    callback = function(value)
        print("seçilen:", value)
    end
})
```

---

## 🎯 Multibox (Çoklu Seçim Listesi)

```lua
Section:multibox({
    name = "seçenekler",
    flag = "secimler",
    options = { "A", "B", "C", "D" },
    default = { "A" },
    max = 3,
    callback = function(secilenler)
        print("aktif olanlar:", table.concat(secilenler, ", "))
    end
})
```

---

## 🎨 ColorPicker (Renk Seçici)

```lua
Section:colorpicker({
    name = "vurgulu renk",
    flag = "accent_renk",
    default = Color3.fromRGB(255, 100, 100),
    callback = function(renk)
        print("seçilen renk:", renk)
    end
})
```

---

## 🎚️ Slider (Kaydırmalı Seçici)

```lua
Section:slider({
    name = "hacim",
    flag = "ses_seviyesi",
    min = 0,
    max = 100,
    default = 50,
    suffix = "%",
    float = 1,
    callback = function(deger)
        print("ses:", deger)
    end
})
```

---

## 🎮 Keybind (Tuş Atama)

```lua
Section:keybind({
    name = "menu aç/kapa",
    flag = "menu_toggle",
    default = Enum.KeyCode.M,
    mode = "Toggle", -- veya "Hold"
    callback = function()
        print("tuşa basıldı")
    end
})
```

---

## 📌 Notlar

* Her element `flag` kullanır. Bu `library.flags["flag_ismi"]` ile erişilebilir.
* `default` alanı, başlangıç değerini belirtir.
* `callback` fonksiyonu, kullanıcı bir işlem yaptığında tetiklenir.
* `section`, `page`, `window` katmanlıdır. Her şey bir `section` içinde olmalıdır.

---

## 🛠 Ekstra

### Divider (Ayırıcı Çizgi)

```lua
Section:divider({ name = "ayar grubu" })
```

---

### Notify (Bildirim)

```lua
library:notify({
    title = "Uyarı",
    text = "İşlem başarılı!",
    time = 5
})
```

---

### Script'e Dışarıdan Erişim

```lua
local Deger = library.flags["ses_seviyesi"]
```

---

## 🧪 Örnek

```lua
local UI = Section:toggle({ name = "test", flag = "acik", default = true })
if library.flags["acik"] then
    print("başlangıçta açıktı")
end
```

```

---

Bu dosyayı `writefile("documentation.md", [[...]])` ile de verebilirim istersen.  
Başka element veya örnek istiyorsan da hemen eklerim.
```
