---

# 🧑‍💻  Git ir GitHub:

## 1. Kas yra Git ir GitHub?

* **Git** – tai versijų valdymo sistema. Ji padeda sekti visus kodo pakeitimus, grįžti prie senesnių versijų, dirbti keliems žmonėms su tuo pačiu projektu.
* **GitHub** – tai debesų platforma, kurioje galima laikyti Git projektus. Ji leidžia pasidalinti projektu su kitais ar tiesiog turėti atsarginę kopiją.

---

# 2. Įrankių paruošimas

1. **Įdiek Git**

   - Atsisiųsk iš [https://git-scm.com/](https://git-scm.com/)
   - Įdiegus, patikrink ar veikia:

     ```bash
     git --version
     ```

2. **Sukurk GitHub paskyrą**

   - Eik į [https://github.com/](https://github.com/)
   - Susikurk paskyrą.

3. **Susiek Git su savo vardu ir el. paštu**
   (tai bus matoma commit istorijoje):

   ```bash
   git config --global user.name "Tavo Vardas"
   git config --global user.email "tavo.el.pastas@example.com"
   ```

4. **Susiek Git su GitHub per SSH**

[Kaip sukurti ir panaudoti SSH raktą](gitHub_ssh.md)

---

## 3. Naujo projekto sukūrimas

### Variantai

1. **Sukurti visiškai naują projektą kompiuteryje**

   ```bash
   mkdir mano-projektas
   cd mano-projektas
   git init
   ```

   Šis `git init` sukurs tuščią Git repozitoriją.

2. **Nusiklonuoti projektą iš GitHub**
   (jei jau yra repozitorija GitHub):

   ```bash
   git clone git@github.com:tavo-vardas/repozitorijos-pavadinimas.git
    cd repozitorijos-pavadinimas
   ```

---

## 4. Failų sekimas ir commit'ai Git'e

Kai turime projektą, reikia pasakyti Git, kokius failus sekti ir saugoti pakeitimus.

1. Sukurk failą:

   ```bash
   echo "Hello Git!" > readme.txt
   ```

2. Patikrink būseną:

   ```bash
   git status
   ```

   Matysi, kad `readme.txt` yra naujas (nesekamas).

3. Pridėk prie sekamų failų:

   ```bash
   git add readme.txt
   ```

4. Sukurk commit'ą:

   ```bash
   git commit -m "Pridėtas pirmas failas readme.txt"
   ```

5. Patikrink commit istoriją:

   ```bash
   git log
   ```

---

## 5. Darbas su GitHub (nuotolinė repozitorija)

1. **Sukurk naują repozitoriją GitHub** (be README, nes jau turime failą).

   - Pasirink „New Repository“.
   - Duok pavadinimą, pvz. `mano-projektas`.

2. **Prijunk vietinį projektą prie GitHub (jei repozitorija nuklonuota, šio žingsnio daryti nereikia)**  
   (čia `tavo-vardas` – tavo GitHub vartotojo vardas):

   ```bash
   git remote add origin git@github.com:tavo-vardas/repozitorijos-pavadinimas.git
   ```

3. **Išsiųsk pakeitimus į GitHub**:

   ```bash
   git push -u origin main
   ```

   > Pastaba: Jei Git sukūrė šaką `master`, ją galima pervadinti:
   >
   > ```bash
   > git branch -M main
   > ```

4. Patikrink GitHub – ten jau bus tavo failai.

---

## 6. Pakeitimų siuntimas ir gavimas

### Jei padarei pakeitimų vietoje

```bash
git add .
git commit -m "Pakeistas failas"
git push
```

### Jei kažkas pakeitė GitHub'e

```bash
git pull
```

---

## 7. Naudingi Git įrankiai (pradedančiajam)

- **Matyti būseną**:

  ```bash
  git status
  ```

- **Matyti paskutinius pakeitimus**:

  ```bash
  git log --oneline
  ```

- **Peržiūrėti kokie pakeitimai atlikti**:

  ```bash
  git diff
  ```

- **Pašalinti failą iš Git**:

  ```bash
  git rm failas.txt
  git commit -m "Ištrintas failas"
  git push
  ```

---

## 8. Pilnas darbo ciklas

1. **Sukurti failą arba pakeisti esamą.**
2. **Pridėti prie Git:**

   ```bash
   git add .
   ```

3. **Sukurti commit:**

   ```bash
   git commit -m "Aprašyk ką padarei"
   ```

4. **Išsiųsti į GitHub:**

   ```bash
   git push
   ```

5. **Atsisiųsti naujausius pakeitimus iš GitHub:**

   ```bash
   git pull
   ```

---

## 9. Praktinė užduotis

1. Sukurk aplanką `git-mokymai`.
2. Inicializuok Git su `git init`.
3. Sukurk failą `dienorastis.txt` ir parašyk jame:

   ```Šiandien išmokau naudotis Git!
   ```

4. Padaryk pirmą commit.
5. Sukurk repozitoriją GitHub ir išsiųsk savo projektą.
6. Pakviesk draugą prisidėti prie repozitorijos, kad jis irgi padarytų pakeitimą.

---
