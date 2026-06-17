# True-3
mahsulotlar = [
    {"nom": "Smartfon", "narx": 500, "soni": 12, "kategoriya": "Elektronika"},
    {"nom": "Noutbuk", "narx": 1200, "soni": 5, "kategoriya": "Elektronika"},
    {"nom": "Televizor", "narx": 800, "soni": 8, "kategoriya": "Elektronika"},
    {"nom": "Krossovka", "narx": 120, "soni": 25, "kategoriya": "Kiyim"},
    {"nom": "Futbolka", "narx": 30, "soni": 50, "kategoriya": "Kiyim"},
    {"nom": "Blender", "narx": 80, "soni": 15, "kategoriya": " texnika"},
    {"nom": "Mikrotolqinli pech", "narx": 150, "soni": 10, "kategoriya": " texnika"},
    {"nom": "Changyutgich", "narx": 200, "soni": 7, "kategoriya": " texnika"},
    {"nom": "Kitob", "narx": 15, "soni": 100, "kategoriya": "Kitoblar"},
    {"nom": "Stol", "narx": 120, "soni": 4, "kategoriya": "Mebel"},
    {"nom": "Stul", "narx": 45, "soni": 20, "kategoriya": "Mebel"},
    {"nom": "Stul", "narx": 50, "soni": 20, "kategoriya": "Zaryadka"},
]

def mahsulotlarni_chiqar(ro_yxat, sarlavha):
    """Natijalarni chiroyli f-string formatda chiqaruvchi yordamchi funksiya"""
    print(f"\n=== {sarlavha} ===")
    print(f"{'Nom':<20} | {'Narx':<8} | {'Soni':<6} | {'Kategoriya':<15}")
    print("-" * 60)
    for m in ro_yxat:
        print(f"{m['nom']:<20} | ${m['narx']:<6} | {m['soni']:<6} | {m['kategoriya']:<15}")


saralangan_oshib = sorted(mahsulotlar, key=lambda p: p['narx'])
mahsulotlarni_chiqar(saralangan_oshib, "Narx bo'yicha saralash (Oshib boruvchi)")

saralangan_kamayuvchi = sorted(mahsulotlar, key=lambda p: p['narx'], reverse=True)
mahsulotlarni_chiqar(saralangan_kamayuvchi, "Narx bo'yicha saralash (Kamayuvchi)")


murakkab_saralash = sorted(mahsulotlar, key=lambda p: (-p['narx'], p['nom']))
mahsulotlarni_chiqar(murakkab_saralash, "Murakkab saralash (Narx ▼, Nomi ▲)")


eng_arzon = min(mahsulotlar, key=lambda p: p['narx'])
eng_qimmat = max(mahsulotlar, key=lambda p: p['narx'])

print(f"\n=== Eng arzon va Eng qimmat mahsulotlar ===")
print(f"📉 Eng arzon: {eng_arzon['nom']} - ${eng_arzon['narx']} ({eng_arzon['kategoriya']})")
print(f"📈 Eng qimmat: {eng_qimmat['nom']} - ${eng_qimmat['narx']} ({eng_qimmat['kategoriya']})")


qidirilayotgan_kategoriya = "Maishiy texnika"
filtrgan_katalog = list(filter(lambda p: p['kategoriya'].lower() == qidirilayotgan_kategoriya.lower(), mahsulotlar))
mahsulotlarni_chiqar(filtrgan_katalog, f"Filtr: '{qidirilayotgan_kategoriya}' kategoriyasi")


qiymatlar_ro_yxati = list(map(lambda p: p['narx'] * p['soni'], mahsulotlar))
umumiy_ombordagi_summa = sum(qiymatlar_ro_yxati)

print(f"\n=== Ombordagi umumiy hisob (map yordamida) ===")
for m, qiy in zip(mahsulotlar, qiymatlar_ro_yxati):
    print(f" - {m['nom']:<18}: {m['soni']:>3} ta x ${m['narx']:<5} = ${qiy:,}")
print("-" * 40)
print(f"💰 Ombordagi barcha mahsulotlarning umumiy qiymati: ${umumiy_ombordagi_summa:,}\n")
