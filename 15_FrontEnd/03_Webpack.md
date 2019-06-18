mkdir -p ~/webpack-test/src ~/webpack-test/public
cd webpack-test
npm init
npm install --save-dev webpack webpack-cli

vi ~/webpack-test/app/index.js

var greeter = require('./Greeter.js');
document.getElementById('root').appendChild(greeter());

vi ~/webpack-test/app/Greeter.js

module.exports = function() {
    var greet = document.createElement('div');
    greet.textContent = "hi there!";
    return greet;
};

vi ~/webpack-test/public/index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Webpack Project</title>
</head>
<body>
    <div id="root"></div>
    <script src="bundle.js"></script>
</body>
</html>

install webpack locally:
cd ~/webpack-test
npm install --save-dev webpack
touch public/bundle.js

create webpack configuration file:
cd ~/webpack-test
vi webpack.config.js

module.exports = {
   entry: __dirname + "/app/main.js",
   output: {
     path: __dirname + "/public",
     filename: "bundle.js"
   }
}
