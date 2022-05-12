# React on Heroku



1. `npx create-react-app react-on-heroku`
2. `cd react-on-heroku`
3. `npm start`
4. `npm install express --save`
5. create `server/server.js`

```
const path = require('path');
const express = require('express');
const app = express();
const publicPath = path.join(__dirname, '..', 'build');
const port = process.env.PORT || 3000;
app.use(express.static(publicPath));
app.get('*', (req, res) => {
   res.sendFile(path.join(publicPath, 'index.html'));
});
app.listen(port, () => {
   console.log('Server is up!');
});

```
6. build and start node server
```
npm run build
node server/server.js
```

7. update `package.json` run script. since heroku will execute `npm run start`

```
"start": "node server/server.js",
"start-dev": "react-scripts start",
```
8. `heroku create react-on-heroku`
9. `git remote -v`
10. `git push heroku master` to deploy

Done
