header {
  background-color: #8B0000;
  color: white;
  padding: 30px 0;
  text-align: center;
}

header h1 {
  font-size: 3em;
  margin: 0;
  letter-spacing: 4px;
  font-weight: 700;
}

header p {
  font-size: 1.2em;
  margin-top: 10px;
  font-style: italic;
  font-weight: 300;
}

nav {
  background-color: #333;
  text-align: center;
  padding: 12px 0;
}

nav a {
  color: white;
  text-decoration: none;
  margin: 0 20px;
  font-size: 1.1em;
  font-weight: 600;
  cursor: pointer;
  transition: color 0.3s;
}

nav a:hover {
  color: #F4A261;
}

section {
  display: none;
  padding: 40px 20px;
  text-align: center;
  background-color: #fefefe;
}

#home {
  display: block;
  padding: 80px 20px;
  background: linear-gradient(135deg, #8B0000 0%, #F4A261 100%);
  color: white;
  text-align: center;
  min-height: 80vh;
  box-sizing: border-box;
}

#home > div {
  max-width: 900px;
  margin: 0 auto;
}

#home h2 {
  font-size: 3.5em;
  margin-bottom: 0.2em;
  font-weight: 700;
  letter-spacing: 2px;
}

#home p.lead {
  font-size: 1.5em;
  margin-bottom: 1em;
  font-style: italic;
  font-weight: 300;
}

#home p.desc {
  font-size: 1.1em;
  max-width: 600px;
  margin: 0 auto 2em auto;
  line-height: 1.6;
}

#home img {
  width: 280px;
  border-radius: 15px;
  margin-bottom: 25px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

#home button {
  background-color: white;
  color: #8B0000;
  border: none;
  padding: 15px 35px;
  font-size: 1.2em;
  font-weight: 600;
  border-radius: 30px;
  cursor: pointer;
  transition: background-color 0.3s;
}

#home button:hover {
  background-color: #f4a261;
  color: white;
}

.menu-item {
  background-color: white;
  width: 280px;
  margin: 15px;
  padding: 20px;
  display: inline-block;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: left;
  cursor: pointer;
  transition: transform 0.2s;
}

.menu-item:hover {
  transform: translateY(-5px);
}

.menu-item h3 {
  margin-top: 0;
  color: #8B0000;
}

.menu-item p {
  color: #666;
}

.menu-item strong {
  color: #F4A261;
}

footer {
  background-color: #8B0000;
  color: white;
  text-align: center;
  padding: 15px 0;
  margin-top: 40px;
}

/* Modal */
.modal {
  display: none;
  position: fixed;
  z-index: 1000;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.6);
}

.modal-content {
  background-color: #fff;
  margin: 5% auto;
  padding: 30px;
  border-radius: 10px;
  width: 90%;
  max-width: 500px;
  position: relative;
  text-align: left;
  box-sizing: border-box;
}

.close {
  color: #aaa;
  position: absolute;
  top: 10px;
  right: 20px;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
}

.close:hover {
  color: #8B0000;
}

.order-button,
.submit-button {
  background-color: #8B0000;
  color: white;
  border: none;
  padding: 12px 20px;
  margin-top: 15px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 600;
  font-size: 1em;
}

.order-button:hover,
.submit-button:hover {
  background-color: #a00000;
}

form input,
form select,
form textarea {
  width: 100%;
  padding: 10px;
  margin-top: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
  font-size: 1em;
  font-family: inherit;
}

.confirmation {
  color: green;
  font-weight: bold;
  margin-top: 20px;
  font-size: 1.1em;
}
