# NodeJS MongoDB connect 


`mkdir ./models
-touch /models/Post.js`
```js
// not 
const mongoose = require("mongoose");
const PostSchema = new mongoose.Schema({
	title: { type: String, require: true },
	content: { type: String, require: true },
	date: { type: Date, default: Date.now },
});
module.exports = mongoose.model("Post", PostSchema);
```




`touch test.js`

```js
  const mongoose = require("mongoose");
  const Post = require("./models/Post");
  require("dotenv").config();

  mongoose.connect(
    process.env.DB_CONNECT,
    {
      useNewUrlParser: true,
      useUnifiedTopology: true,
    }
  );

  Post.create(
    {
      title: "Baslik",
      content: "İcerik",
    },
    (error, post) => {
      console.log(error, post);
    }
  );
```
	
`app.js`

```js
	const express = require("express");
	const { engine } = require("express-handlebars");
	const app = express();
	const port = 3000;
	const hostname = "127.0.0.1";
	const mongoose = require("mongoose");
	const Handlebars = require("handlebars");
	const { allowInsecurePrototypeAccess, } = require("@handlebars/allow-prototype-access");

	mongoose.connect("mongodb://127.0.0.1/nodeblog_db", {
	  useNewUrlParser: true,
	  useUnifiedTopology: true,
	  handlebars: allowInsecurePrototypeAccess(Handlebars),
	});

	app.engine("hbs", engine({ extname: ".hbs", defaultLayout: "main" }));
	app.set("view engine", "hbs");
```
