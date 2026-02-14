# UNLOX-MAJOR-PROJECT
#THIS IS A MAJOR PROJECT OF MY WEB DEVELOPMENT COURSE FROM UNLOX.

#PROJECT STRUCTURE
corporate-website/
│
├── frontend/
│   ├── pages/
│   │     index.js
│   │     about.js
│   │     services.js
│   │     portfolio.js
│   │     contact.js
│   ├── components/
│   │     Navbar.js
│   │     Hero.js
│   │     ServiceCard.js
│   │     Footer.js
│   └── styles/
│
├── backend/
│   ├── server.js
│   ├── routes/
│   │      contactRoutes.js
│   ├── models/
│   │      Contact.js
│   └── config/
│          db.js

# FRONTEND CODE (Next.js)
 #Navbar Component 
 
import Link from "next/link";

export default function Navbar() {
  return (
    <nav className="nav">
      <h2>Outpro.India</h2>

      <div>
        <Link href="/">Home</Link>
        <Link href="/about">About</Link>
        <Link href="/services">Services</Link>
        <Link href="/portfolio">Portfolio</Link>
        <Link href="/contact">Contact</Link>
      </div>
    </nav>

#HOME PAGE

import Navbar from "../components/Navbar";

export default function Home() {
  return (
    <>
      <Navbar />

      <section className="hero">
        <h1>Building Digital Corporate Identity</h1>
        <p>Modern scalable web solutions for businesses.</p>
        <button>Get Started</button>
      </section>

      <section>
        <h2>Our Services</h2>
        <ul>
          <li>Web Development</li>
          <li>UI/UX Design</li>
          <li>SEO Optimization</li>
        </ul>
      </section>
    </>
  );
}

#SERVICES PAGE
export default function Services() {
  return (
    <div>
      <h1>Our Services</h1>

      <div>
        <h3>Website Development</h3>
        <p>Responsive and scalable corporate websites.</p>
      </div>

      <div>
        <h3>Digital Marketing</h3>
        <p>Lead generation focused marketing strategies.</p>
      </div>
    </div>
  );
}

#BACKEND
#server.js
const express = require("express");
const mongoose = require("mongoose");
const cors = require("cors");

const contactRoutes = require("./routes/contactRoutes");

const app = express();

app.use(cors());
app.use(express.json());

mongoose.connect("mongodb://127.0.0.1:27017/outpro");

app.use("/api/contact", contactRoutes);

app.listen(5000, () => {
  console.log("Server running on port 5000");
});

#CONTACT MODEL
const mongoose = require("mongoose");

const ContactSchema = new mongoose.Schema({
  name: String,
  email: String,
  message: String,
});

module.exports = mongoose.model("Contact", ContactSchema);

#CONTACT ROUTES
const express = require("express");
const router = express.Router();
const Contact = require("../models/Contact");

router.post("/", async (req, res) => {
  try {
    const newContact = new Contact(req.body);
    await newContact.save();
    res.json({ message: "Message Saved Successfully" });
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

module.exports = router;


#PERFORMANCE OPTIMISATION

Implement:
1. Lazy loading images
2. Image optimization
3.Minified CSS
4.CDN (Cloudflare)
5.Next.js Image component

#ANALYTICS INTEGRATION

import Script from "next/script";

<Script
 src="https://www.googletagmanager.com/gtag/js?id=GA_ID"
/>

# Folder Structure 

  outpro-project/
   frontend-nextjs/
   backend-nodejs/

  # Creating .env file
 #FRONT-END
   NEXT_PUBLIC_API_URL=https://your-backend.onrender.com
#BACK-END
  MONGO_URI=your_mongodb_atlas_url
PORT=5000

  





































    
  );
}
