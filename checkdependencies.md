1. make sure all necessary dependencies are installed
```bash
npm install
```
2. sometimes clearing the cache can help
```bash
npm cache clean --force
npm install
```
3. ensure node.js module is compatible
<br> if unsure:
```bash
nvm use stable
```
<br>check ur node version
```bash
node -v
```
4. check if the issue is specific to your vercel or project
```bash
npm run build
```
