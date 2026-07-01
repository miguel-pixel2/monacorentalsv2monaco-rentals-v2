# 🚀 Déploiement sur Vercel

## ✅ Prérequis
- ✅ Compte GitHub (code poussé)
- ✅ Compte Vercel
- ✅ Supabase configuré
- ✅ Cloudinary configuré

## 📋 Étapes de déploiement

### 1. **Pousser le code sur GitHub**
```bash
cd C:\Dev\monaco-rentals-v2
git init
git add .
git commit -m "Initial commit - Monaco Rentals"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/monaco-rentals-v2.git
git push -u origin main
```

### 2. **Connecter GitHub à Vercel**
1. Aller sur https://vercel.com/new
2. **Importer un repository GitHub**
3. Sélectionner `monaco-rentals-v2`
4. Cliquer **Import**

### 3. **Configurer les variables d'environnement dans Vercel**

Dans la section "Environment Variables", ajouter:

```
NEXT_PUBLIC_SUPABASE_URL=https://sinwrgxwuvosypgwhvjc.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=bfchpiry
CLOUDINARY_API_KEY=892868755433479
CLOUDINARY_API_SECRET=1G2v_hqA5r-6PCO6i3ot8cM_Uhg
NEXT_PUBLIC_ADMIN_PASSWORD=Admin123!
RESEND_API_KEY=re_your_key_here
ADMIN_EMAIL=admin@monacorentals.com
```

### 4. **Cliquer "Deploy"**
Vercel va:
- Cloner votre code
- Installer les dépendances (`npm install`)
- Builder le projet (`npm run build`)
- Héberger sur un domaine unique

### 5. **Accéder à votre site**
- URL: `https://votre-projet.vercel.app`
- Admin: `https://votre-projet.vercel.app/admin/login`
- Photos: `https://votre-projet.vercel.app/admin/photos`

---

## 🔒 Admin Access

**Login**
- URL: `/admin/login`
- Password: `Admin123!` (changeable dans `.env`)

**Dashboard**
- URL: `/admin/dashboard`
- Affiche les stats de réservation

**Photo Management**
- URL: `/admin/photos`
- Upload jusqu'à 10 photos par propriété
- Gestion des catégories et ordre d'affichage

---

## 🌐 URL du site
Après déploiement, votre site sera accessible à:
```
https://votre-projet.vercel.app
```

Partagez cette URL avec les patrons pour tests!

---

## 🐛 Troubleshooting

### Build fails avec erreurs TypeScript
- Vérifiez que les variables d'environnement sont correctes
- Regardez les logs Vercel dans le dashboard

### Photos ne s'affichent pas
- Vérifiez les credentials Cloudinary
- Testez sur `/admin/photos`

### Erreur de connexion Supabase
- Vérifiez que `NEXT_PUBLIC_SUPABASE_URL` est correct
- Vérifiez que les clés de service sont valides

---

## 📞 Support
En cas de problème, consultez:
- https://vercel.com/docs
- https://supabase.com/docs
- https://next.js.org/docs
