# Mobexler Android Lab Setup

##  Description

Ce laboratoire présente l’installation et la configuration de l’environnement Mobexler dans VirtualBox pour les travaux pratiques de sécurité Android.

Le setup inclut :

* Import de la VM Mobexler (.OVA)
* Configuration réseau NAT + Host-Only
* Vérification des interfaces réseau
* Utilisation d’un émulateur Android Studio
* Configuration et tests ADB
* Création d’un snapshot baseline

---

# Technologies utilisées

* Oracle VirtualBox
* Mobexler VM
* Android Studio Emulator
* ADB (Android Debug Bridge)
* Windows Host

---

#  Prérequis

* VirtualBox installé
* Virtualisation activée (VT-x / AMD-V)
* Android Studio
* RAM ≥ 4 GB
* Espace disque ≥ 25 GB

---

#  Étape 1 — Import de Mobexler

<img width="566" height="296" alt="image" src="https://github.com/user-attachments/assets/f02a4bcf-49ab-4ef3-8beb-fc1a56cee0a1" />

## Configuration réalisée

* Import Appliance
* Sélection du fichier `Mobexler.ova`
* Création automatique de la VM




---

# 🌐 Étape 2 — Configuration réseau

## Adapter 1

* Mode : NAT

## Adapter 2

* Mode : Host-Only Adapter

Configuration utilisée :

```text
Adapter 1 → NAT
Adapter 2 → Host-Only
```


➡️ Capture de `Settings → Network` dans VirtualBox montrant :

* NAT
* Host-Only Adapter
<img width="824" height="207" alt="image" src="https://github.com/user-attachments/assets/987569ff-1bb7-4702-9382-f319da40143c" />

---

# 🔍 Étape 3 — Vérification des interfaces réseau

Commande utilisée :

```bash
ip a
```

Interfaces détectées :

* `enp0s8`
* `enp0s17`

<img width="664" height="308" alt="image" src="https://github.com/user-attachments/assets/0ed503e2-538f-4869-8f38-37c914bcf8e4" />



---

# 📱 Étape 4 — Configuration Android Emulator

Émulateur utilisé :

```text
Android Studio Emulator
```

Vérification du device :

```powershell
adb devices
```

Résultat :

```text
emulator-5554    device
```

## 📸 Screenshot à insérer ici

➡️ Capture de :

* Android Emulator lancé
 <img width="223" height="501" alt="image" src="https://github.com/user-attachments/assets/b4b8731b-1d64-40ec-bd92-d43a6d1c8229" />

* résultat de `adb devices`
  <img width="386" height="59" alt="image" src="https://github.com/user-attachments/assets/7b14f278-bf05-454a-b022-821566c2ef2a" />


---

# 🔧 Étape 5 — Tests ADB

Tests de communication entre Mobexler et Android Emulator.

Commande testée :

```bash
adb connect 192.168.156.1:5555
```

Commande de vérification :

```bash
adb devices
```



➡️ Capture :

* `adb connect`
* `adb devices`
* messages d’erreur éventuels

---
<img width="940" height="507" alt="image" src="https://github.com/user-attachments/assets/15288341-f878-424a-826a-93c8aa77f8ff" />
<img width="919" height="532" alt="image" src="https://github.com/user-attachments/assets/74609f3d-1655-4ec7-b3be-fe14fa2c7773" />

# ⚠️ Problème rencontré

Un conflit de versions et de ports ADB a été observé entre :

* Windows
* Android Studio Emulator
* Mobexler
* VirtualBox

Ports concernés :

```text
5037
5555
```

Cela empêche l’établissement complet d’une connexion distante ADB depuis Mobexler.

Cependant :

* l’émulateur Android fonctionne correctement
* ADB fonctionne côté Windows
* l’environnement reste prêt pour les futurs TP


<img width="920" height="532" alt="image" src="https://github.com/user-attachments/assets/7d481511-ec85-4e89-be1c-fdd66eb21003" />


---

# 💾 Étape 6 — Création du Snapshot

Snapshot créé :

```text
CLEAN_BASELINE_TP1
```

Permet de restaurer rapidement un environnement propre avant les futurs labs.
<img width="951" height="458" alt="image" src="https://github.com/user-attachments/assets/527acde3-77c9-49ba-acc3-8ac415e19f0a" />



---

# ✅ Conclusion

Le laboratoire Mobexler a été installé et configuré avec succès dans VirtualBox.

Les interfaces réseau NAT et Host-Only ont été correctement mises en place et vérifiées.

L’environnement Android Studio Emulator ainsi que les outils ADB sont opérationnels pour les futurs travaux pratiques de sécurité Android.

---
