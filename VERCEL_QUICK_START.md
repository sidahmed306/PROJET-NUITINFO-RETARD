# 🚀 Déploiement Rapide sur Vercel

Votre projet est maintenant sur GitHub : **https://github.com/sidahmed306/projet_nuitInfo_retard**

## 📋 Étapes pour déployer sur Vercel

### Étape 1 : Créer un compte Vercel

1. Allez sur **https://vercel.com**
2. Cliquez sur **"Sign Up"**
3. Choisissez **"Continue with GitHub"**
4. Autorisez Vercel à accéder à votre compte GitHub

### Étape 2 : Déployer le Frontend (Client)

1. Dans le dashboard Vercel, cliquez sur **"Add New Project"**
2. Importez votre repository : **`sidahmed306/projet_nuitInfo_retard`**
3. Configuration du projet :
   - **Framework Preset** : `Create React App`
   - **Root Directory** : `client` ⚠️ **IMPORTANT**
   - **Build Command** : `npm run build`
   - **Output Directory** : `build`
   - **Install Command** : `npm install`
4. Variables d'environnement (cliquez sur "Environment Variables") :
   - **Name** : `REACT_APP_API_URL`
   - **Value** : `http://localhost:4001/api` (pour l'instant, on changera après)
   - Cliquez sur **"Add"**
5. Cliquez sur **"Deploy"**

⏳ Attendez que le déploiement se termine (2-3 minutes)

### Étape 3 : Déployer le Backend

**⚠️ IMPORTANT :** Pour le backend avec SQLite, utilisez **Railway** au lieu de Vercel (voir ci-dessous).

#### Option A : Railway (Recommandé) ✅

1. Allez sur **https://railway.app**
2. Cliquez sur **"Start a New Project"**
3. Choisissez **"Deploy from GitHub repo"**
4. Sélectionnez votre repository : `projet_nuitInfo_retard`
5. Railway va détecter automatiquement le projet
6. Cliquez sur les **"..."** à côté du service → **"Settings"**
7. Dans **"Root Directory"**, entrez : `server`
8. Variables d'environnement (onglet "Variables") :
   ```
   PORT=4001
   JWT_SECRET=votre-secret-jwt-super-securise-changez-moi-12345
   JWT_EXPIRES_IN=24h
   NODE_ENV=production
   FRONTEND_URL=https://votre-frontend.vercel.app
   ```
9. Railway générera une URL (ex: `https://votre-app.railway.app`)
10. Copiez cette URL

#### Option B : Vercel (Non recommandé pour SQLite)

Si vous voulez quand même utiliser Vercel :

1. Créez un **nouveau projet** sur Vercel
2. Importez le même repository
3. Configuration :
   - **Root Directory** : `server`
   - **Framework Preset** : `Other`
4. Variables d'environnement :
   ```
   PORT=4001
   JWT_SECRET=votre-secret-jwt-changez-moi
   JWT_EXPIRES_IN=24h
   NODE_ENV=production
   FRONTEND_URL=https://votre-frontend.vercel.app
   ```
5. Déployez

### Étape 4 : Mettre à jour l'URL du Backend dans le Frontend

1. Retournez sur Vercel → votre projet frontend
2. Allez dans **"Settings"** → **"Environment Variables"**
3. Modifiez `REACT_APP_API_URL` avec l'URL de votre backend :
   - Si Railway : `https://votre-app.railway.app/api`
   - Si Vercel : `https://votre-backend.vercel.app/api`
4. Allez dans **"Deployments"** → Cliquez sur **"..."** → **"Redeploy"**

### Étape 5 : Vérifier que tout fonctionne

1. **Frontend** : Visitez `https://votre-frontend.vercel.app`
2. **Backend** : Visitez `https://votre-backend.railway.app/api` ou `https://votre-backend.vercel.app/api`
   - Vous devriez voir : `{"ok": true, "message": "API is running"}`

## ✅ Résumé des URLs

- **GitHub** : https://github.com/sidahmed306/projet_nuitInfo_retard
- **Frontend Vercel** : `https://votre-frontend.vercel.app`
- **Backend Railway** : `https://votre-app.railway.app` (recommandé)
- **Backend Vercel** : `https://votre-backend.vercel.app` (non recommandé)

## 🔄 Mises à jour futures

Quand vous modifiez le code :

```powershell
git add .
git commit -m "Description des changements"
git push origin main
```

Vercel et Railway déploieront automatiquement les nouvelles versions !

## 🆘 Problèmes courants

### Le backend ne fonctionne pas sur Vercel
→ Utilisez Railway à la place (gratuit et mieux pour SQLite)

### Erreurs CORS
→ Vérifiez que `FRONTEND_URL` dans le backend correspond à l'URL de votre frontend Vercel

### Le frontend ne peut pas se connecter au backend
→ Vérifiez que `REACT_APP_API_URL` est correctement configuré dans Vercel

## 📞 Besoin d'aide ?

Consultez les guides détaillés :
- `GITHUB_DEPLOY.md` - Guide rapide
- `DEPLOYMENT_GUIDE.md` - Guide complet

