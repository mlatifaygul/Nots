# NodeJS MongoDB connect 

[ MongoDB => 
mkdir ./models/Post.js => {
	const mongoose = require("mongoose");

	const PostSchema = new mongoose.Schema({
  	title: { type: String, require: true },
  	content: { type: String, require: true },
  	date: { type: Date, default: Date.now },
	});

	module.exports = mongoose.model("Post", PostSchema);
}
touch test.js => {
	const mongoose = require("mongoose");
	const Post = require("./models/Post");

	mongoose.connect(
  	"mongodb+srv://arin:toor@nodedemo.b8xph.mongodb.net/ariNode?retryWrites=true&w=majority",
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
}
app.js => {
const express = require("express");
const { engine } = require("express-handlebars");
const app = express();
const port = 3000;
const hostname = "127.0.0.1";
const mongoose = require("mongoose");

mongoose.connect("mongodb://127.0.0.1/nodeblog_db", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

app.engine("hbs", engine({ extname: ".hbs", defaultLayout: "main" }));
app.set("view engine", "hbs");
} ]
