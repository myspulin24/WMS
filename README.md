# 📦 WMS Project

**WMS Project** je univerzální desktopová aplikace pro řízení a sledování skladových operací (Warehouse Management System).  
Cílem projektu je **zrychlit** tok zboží, **snížit chybovost** a poskytnout **přehledné nástroje** pro operativu i správu skladu.

---

## ✨ Co aplikace dělá

- Umožňuje **příjem, výdej a přesuny položek** mezi lokacemi s průběžnou validací vstupů.  
- Nabízí **rychlé přehledy** zásob, pozic a stavu položek s podporou filtrování a práce z klávesnice.  
- Poskytuje nástroje pro **vyhledání volného místa** a jeho **alokaci** dle pravidel (např. typ lokace, kapacita).  
- Je navržena pro **rozšíření** – exporty, logování, integraci s ERP a další funkce.

---

## 🧱 Technologie (přehled)

| Vrstva | Technologie / Framework | Popis |
|--------|--------------------------|--------|
| **Frontend (UI)** | .NET WinForms (VB.NET) | Formuláře, datové mřížky (DataGridView), validace vstupů. |
| **Datová logika** | ADO.NET, T-SQL | Datové operace, transakce, kontrolní dotazy (bez vendor lock-inu). |
| **Databáze** | MS SQL Server | Úložiště skladových entit (položky, lokace, pohyby). |
| **Exportní nástroje** | OpenXML SDK | (volitelně) Excel exporty včetně formátování. |
| **Logování** | System.IO, EventLog | Sledování chyb a audit významných akcí. |

---

## 🧩 Komponenty a kód 

### Warehouse.vb
- **Typ**: Třída (Warehouse)
- **Importy**: System.Configuration, System.Convert, System.Data, System.Data.Common, System.Runtime.InteropServices, System.Threading.Tasks, System.IO, System.Diagnostics…
- **Veřejné funkce**: FindControlRecursive, MakeInlineTextCell, MakeStyledCell, GetExcelColumnName, MakeAutoCell
- **Procedury (Sub)**: Warehouse_Load, SaveControlLayout, Warehouse_Resize, ResizeControls, TestConnection, TreeView1_BeforeCollapse, B_Konec_Click, TabControl1_SelectedIndexChanged…
- **Události**: Warehouse_Load (handles MyBase.Load), Warehouse_Resize (handles MyBase.Resize), TreeView1_BeforeCollapse (handles TreeView1.BeforeCollapse), B_Konec_Click (handles B_Konec.Click), TabControl1_SelectedIndexChanged (handles TabControl1.SelectedIndexChanged), TreeView1_AfterSelect (handles TreeView1.AfterSelect), PictureBox1_MouseMove (handles PictureBox1.MouseMove), PictureBox_StackMode_Paint (handles PictureBox_StackMode.Paint)…
- **Specifika**: Práce s tabulkovými přehledy (DataGridView), Operace nad databází (SQL/ADO.NET), Exporty do Excelu (OpenXML)


### FormPresunPolozek.vb
- **Typ**: Modul / kódový soubor
- **Procedury (Sub)**: New, txtInput1_KeyDown, txtInput2_KeyDown
- **Události**: txtInput1_KeyDown (handles txtInput1.KeyDown), txtInput2_KeyDown (handles txtInput2.KeyDown)


### FormVolneMisto.vb
- **Typ**: Modul / kódový soubor
- **Procedury (Sub)**: New, CloseForm


---

## 🔎 Rychlý souhrn 

### Warehouse.vb
- Počet řádků: **1539**
- Třídy: Warehouse
- Sub procedury (19): Warehouse_Load, SaveControlLayout, Warehouse_Resize, ResizeControls, TestConnection, TreeView1_BeforeCollapse, B_Konec_Click, TabControl1_SelectedIndexChanged, TreeView1_AfterSelect, PictureBox1_MouseMove, PictureBox_StackMode_Paint, CheckBox_StackMode_CheckedChanged…
- Funkce (5): FindControlRecursive, MakeInlineTextCell, MakeStyledCell, GetExcelColumnName, MakeAutoCell
- Události/Handlers (11): Warehouse_Load → MyBase.Load, Warehouse_Resize → MyBase.Resize, TreeView1_BeforeCollapse → TreeView1.BeforeCollapse, B_Konec_Click → B_Konec.Click, TabControl1_SelectedIndexChanged → TabControl1.SelectedIndexChanged, TreeView1_AfterSelect → TreeView1.AfterSelect, PictureBox1_MouseMove → PictureBox1.MouseMove, PictureBox_StackMode_Paint → PictureBox_StackMode.Paint, CheckBox_StackMode_CheckedChanged → CheckBox_StackMode.CheckedChanged, ToolStripMenu_Update_Click → ToolStripMenu_Update.Click…
- Detekované technologie: DataGridView, SQL, OpenXML


### FormPresunPolozek.vb
- Počet řádků: **53**
- Sub procedury (3): New, txtInput1_KeyDown, txtInput2_KeyDown
- Události/Handlers (2): txtInput1_KeyDown → txtInput1.KeyDown, txtInput2_KeyDown → txtInput2.KeyDown


### FormVolneMisto.vb
- Počet řádků: **51**
- Sub procedury (2): New, CloseForm


---

## 🕒 Časová osa vývoje

| Fáze | Období | Popis |
|------|---------|--------|
| **Analýza a návrh** | červenec 2025 | Mapování skladových procesů, návrh obrazovek a stavových toků (příjem, přesun, vychystání, inventura). Specifikace datových struktur a validačních pravidel. |
| **Základní implementace (Warehouse)** | srpen 2025 | Vytvoření základní logiky v **Warehouse.vb** (modely, operace nad položkami, propojení na datovou vrstvu). První prototypy formulářů a práce s tabulkovými přehledy. |
| **Operativní moduly (Přesun, Volné místo)** | září 2025 | Implementace **FormPresunPolozek.vb** (workflow přesunu položek mezi lokacemi včetně kontrol) a **FormVolneMisto.vb** (vyhledávání a přidělení volných pozic). |
| **Testování, výkon, UX** | říjen 2025 | Zátěžové testy nad reálnými daty, ladění validací, zrychlení načítání seznamů a stability při delším provozu. Doplnění logování, ošetření chybových stavů a vylepšení UX (klávesové zkratky, výchozí focus aj.). |
| **Stabilizace a pokračující vývoj** | listopad 2025 – dosud | Řešení uživatelských podnětů, další optimalizace a rozšiřování funkcí podle provozních potřeb. Příprava na širší nasazení a integrace do firemních procesů. |

> 📅 Vývoj: **07/2025 – 11/2025, pokračuje dál (ongoing)**

---

## 🚀 Instalace a spuštění

1. Nainstaluj **.NET Framework 4.8** (nebo novější).  
2. Zajisti připojení k **MS SQL Server** s odpovídajícími oprávněními.  
3. Spusť distribuovaný binární soubor aplikace.  
4. Přihlaš se pod přiděleným účtem a pracuj s přehledy a operacemi skladu.

---

## 📄 Licence a autor

Copyright © 2025 **Michal Jašek**  
Software je ve vývoji, určen pro interní/demonstrativní použití.  
Šíření či komerční využití mimo dohodnuté podmínky není dovoleno.

---

> *„Jednoduchost a spolehlivost jsou klíčem k efektivnímu skladu.“*  
> — Michal Jašek
