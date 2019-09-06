# 서버 CORS 설정하기

- `npm i cors`

```js
const cors = require('cors');

var corsOptions = {
  origin: 'http://example.com',
  optionsSuccessStatus: 200,
};

app.use(cors());


```

