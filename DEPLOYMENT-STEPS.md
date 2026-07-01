# 📋 Étapes de déploiement - Sans Git

**Objectif:** Déployer Monaco Rentals sur Vercel en 5 minutes

---

## Option 1: Via GitHub Desktop (Recommandé - Le plus simple!)

### ✅ Prérequis
- ✅ GitHub Desktop installé: https://desktop.github.com/
- ✅ Compte GitHub
- ✅ Ce dossier prêt

### 📝 Étapes

1. **Ouvrir GitHub Desktop**
2. **File → Add Local Repository**
3. **Sélectionner le dossier:** `C:\Dev\monaco-rentals-v2`
4. **Cliquer "Add Repository"**
5. **En bas à gauche:**
   - Current Branch: créer une branche "main"
6. **Remplir le formulaire:**
   - Summary: `Initial commit`
   - Description: `Monaco Rentals booking system`
7. **Cliquer "Commit to main"**
8. **Cliquer "Publish repository"**
   - Name: `monaco-rentals-v2`
   - Description: `Luxury property booking system for Azores`
   - Laisser Public cochée ✓
9. **Cliquer "Publish Repository"** → Terminé! ✓

Ton repo est maintenant sur GitHub! 🎉

---

## Option 2: Via Git Command Line (Si Git installé)

```bash
cd C:\Dev\monaco-rentals-v2

# Initialiser git
git init
git add .
git commit -m "Initial commit - Monaco Rentals"

# Créer la branche main
git branch -M main

# Ajouter le remote (remplacer USERNAME)
git remote add origin https://github.com/USERNAME/monaco-rentals-v2.git

# Pousser
git push -u origin main
```

---

## Configurer Vercel (Après GitHub)

### 1️⃣ **Aller sur Vercel**
https://vercel.com/new

### 2️⃣ **Sélectionner GitHub**
- Cliquer "Import Git Repository"
- Chercher `monaco-rentals-v2`
- Cliquer "Import"

### 3️⃣ **Configurer le projet**
- Project Name: `monaco-rentals-v2`
- Framework: `Next.js` (détecté auto ✓)
- Laisser les defaults

### 4️⃣ **Ajouter les variables d'environnement**

Cliquer **"Environment Variables"** et ajouter:

```
NEXT_PUBLIC_SUPABASE_URL = https://sinwrgxwuvosypgwhvjc.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
SUPABASE_SERVICE_ROLE_KEY = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME = bfchpiry
CLOUDINARY_API_KEY = 892868755433479
CLOUDINARY_API_SECRET = 1G2v_hqA5r-6PCO6i3ot8cM_Uhg
NEXT_PUBLIC_ADMIN_PASSWORD = Admin123!
RESEND_API_KEY = (ta clé Resend)
ADMIN_EMAIL = admin@monacorentals.com
```

### 5️⃣ **Cliquer "Deploy"**

Vercel va:
- Cloner ton repo
- Installer les dépendances
- Builder le projet
- Déployer en ligne ✓

**⏳ Attendre 2-3 minutes** → Site en ligne! 🚀

---

## 🎉 Résultat final

```
Accès aux différentes pages:

1. Site public:
   https://monaco-rentals-v2.vercel.app

2. Admin Login:
   https://monaco-rentals-v2.vercel.app/admin/login
   Password: Admin123!

3. Photo Management:
   https://monaco-rentals-v2.vercel.app/admin/photos

4. Dashboard:
   https://monaco-rentals-v2.vercel.app/admin/dashboard
```

---

## 🆘 En cas de problème

### Build échoue?
- Vérifier les variables d'environnement dans Vercel
- Vérifier la console Vercel pour les erreurs

### Photos ne s'affichent pas?
- Vérifier les credentials Cloudinary
- Vérifier que la table `rental_images` existe dans Supabase

### Admin ne peut pas se connecter?
- Vérifier le password dans les env vars
- Vérifier localStorage dans le navigateur

---

## 📞 Support
- Vercel Docs: https://vercel.com/docs
- Next.js Docs: https://nextjs.org/docs
- Supabase Docs: https://supabase.com/docs
