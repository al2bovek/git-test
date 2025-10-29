# GitHub SSH raktų naudojimas

## 1. Kas yra SSH raktai?

* **SSH raktas** – tai tarsi skaitmeninis raktas, leidžiantis tavo kompiuteriui prisijungti prie GitHub be slaptažodžio.
* Jį sudaro dvi dalys:

  * **Privatus raktas** (lieka tavo kompiuteryje, niekam jo nerodyk).
  * **Viešas raktas** (įdedamas į GitHub paskyrą).

---### Kaip atrodo viešas raktas?

Viešas raktas yra **visa eilutė** (viena ilga eilutė teksto), pvz.:

```ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEH18u4ipxJLaEc7WLqYZacd+BGsY0Gor1swmdDZ1B7t tavo.el.pastas@example.com
```

Jį sudaro:

* `ssh-ed25519` (rakto tipas),
* ilga simbolių eilutė (pats raktas),
* tavo el. paštas (komentaras, gali būti arba nebūti).

---

## 2. Patikrink ar jau turi SSH raktą

Atidaryk terminalą ir parašyk:

```bash
ls -al ~/.ssh
```

Jei matai failus `id_rsa` ir `id_rsa.pub` (arba `id_ed25519` / `id_ed25519.pub`), raktai jau egzistuoja.

---

## 3. Naujo SSH rakto sukūrimas

Jei raktų nėra arba nori sukurti naują, paleisk:

```bash
ssh-keygen -t ed25519 -C "tavo.el.pastas@example.com"
```

> Jei tavo sistema nepalaiko `ed25519`, naudok:
>
> ```bash
> ssh-keygen -t rsa -b 4096 -C "tavo.el.pastas@example.com"
> ```

Tada:

* Spaudi **Enter**, kad saugotų į numatytą vietą (`~/.ssh/id_ed25519`).
* Galima įrašyti slaptafrazę (papildomam saugumui) arba palikti tuščią.

---

## 4. Paleisk SSH agentą

Norint, kad Git žinotų apie raktą, reikia paleisti agentą:

```bash
eval "$(ssh-agent -s)"
```

Pridėk raktą į agentą:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## 5. Viešo rakto pridėjimas į GitHub

Nukopijuok viešą raktą:

```bash
cat ~/.ssh/id_ed25519.pub
```

* Eik į [GitHub → Settings → SSH and GPG keys](https://github.com/settings/keys).
* Spausk **New SSH key**.
* Įklijuok nukopijuotą raktą.
* Išsaugok.

---## 6. Patikrink prisijungimą

Parašyk:

```bash
ssh -T git@github.com
```

Pirmą kartą paklaus „Are you sure you want to continue connecting?“ – rašyk `yes`.
Jei viskas gerai, pamatysi:

```Hi tavo-vardas! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## 7. Naudojimas su Git

Kai klonuosi projektą, naudok **SSH adresą**, o ne HTTPS.

Pvz.:

```bash
git clone git@github.com:tavo-vardas/mano-projektas.git
```

Kai atliksi `git push` ar `git pull`, GitHub tavęs nebeklaus slaptažodžio.

---

## 8. Naudingi patarimai

* Jei turi kelias GitHub paskyras, gali turėti kelis raktus (`id_ed25519_github`, `id_ed25519_darbas`).
* Tokiu atveju reikia redaguoti `~/.ssh/config` failą, pvz.:

```txt
Host github.com
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519_github
```

---

Dabar gali patogiai jungtis prie GitHub su SSH – nereikės kiekvieną kartą vesti slaptažodžio.
