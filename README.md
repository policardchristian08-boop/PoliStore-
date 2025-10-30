# PoliStore-
E-commerce vente de produits en ligne 
import { useState } from "react";
import { motion } from "framer-motion";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function PoliStore() {
  const [page, setPage] = useState("home");

  const handleOrder = (productName) => {
    const phoneRD = "+18494855079";
    const phoneRH = "+50955339204";
    const message = encodeURIComponent(
      `Bonjour PoliStore 👋, je souhaite commander: ${productName}`
    );
    window.open(`https://wa.me/${phoneRD}?text=${message}`, "_blank", "noopener,noreferrer");
  };

  const products = {
    Parfums: [
      { name: "Élixir de Parfum", desc: "Parfum concentré de luxe.", img: "https://images.unsplash.com/photo-1599058917212-d750089bc07b" },
      { name: "Eau de Toilette", desc: "Fraîcheur et élégance.", img: "https://images.unsplash.com/photo-1599058917212-d750089bc07b" },
      { name: "Eau de Cologne", desc: "Pour homme et femme.", img: "https://images.unsplash.com/photo-1600180758890-6a6a2cfda9e9" },
      { name: "Spray Vaporisateur", desc: "Pratique et léger.", img: "https://images.unsplash.com/photo-1600180758890-6a6a2cfda9e9" },
      { name: "Élixir", desc: "Petite fiole parfumée.", img: "https://images.unsplash.com/photo-1599058917212-d750089bc07b" },
    ],
    Soins: [
      { name: "Savon Naturel", desc: "Pour une peau douce et parfumée.", img: "https://images.unsplash.com/photo-1590796583326-26c9bde0b4ac" },
      { name: "Déodorant Spray", desc: "Longue durée et fraîcheur garantie.", img: "https://images.unsplash.com/photo-1600180758890-6a6a2cfda9e9" },
      { name: "Huile pour Chicha", desc: "Parfum agréable et doux.", img: "https://images.unsplash.com/photo-1600180758890-6a6a2cfda9e9" },
    ],
    Mode: [
      { name: "Tennis US Style", desc: "Mode américaine originale.", img: "https://images.unsplash.com/photo-1528701800489-20be0e7e62c5" },
      { name: "T-shirts importés", desc: "Tissus premium des États-Unis.", img: "https://images.unsplash.com/photo-1521334884684-d80222895322" },
    ],
    Nutrition: [
      { name: "Mass Gainer 5kg", desc: "Pour une prise de masse efficace.", img: "https://images.unsplash.com/photo-1627308595229-7830a5c91f9f" },
    ],
    Téléphones: [
      { name: "iPhone 13 Pro Max", desc: "Appareil original venu des États-Unis.", img: "https://images.unsplash.com/photo-1631422938316-7330e80b3153" },
    ],
  };

  return (
    <div className="min-h-screen bg-white text-gray-900">
      {/* Navbar */}
      <header className="p-6 shadow-md flex justify-between items-center bg-white sticky top-0 z-50">
        <h1 className="text-2xl font-bold text-blue-800">PoliStore</h1>
        <nav className="space-x-4">
          <button
            onClick={() => setPage("home")}
            className={`font-semibold ${page === "home" ? "text-blue-700" : "text-gray-700"}`}
          >
            Accueil
          </button>
          <button
            onClick={() => setPage("products")}
            className={`font-semibold ${page === "products" ? "text-blue-700" : "text-gray-700"}`}
          >
            Produits
          </button>
        </nav>
      </header>

      {/* Home */}
      {page === "home" && (
        <>
          <section className="text-center py-16 bg-gradient-to-b from-blue-50 to-white">
            <motion.h2
              initial={{ opacity: 0, y: -20 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.8 }}
              className="text-4xl font-extrabold mb-4 text-blue-900"
            >
              Le luxe des parfums américains, livrés en Haïti et RD
            </motion.h2>
            <p className="text-gray-700 mb-6">
              Commandez vos parfums, vêtements, accessoires, protéines, téléphones et plus encore.
            </p>
            <Button
              onClick={() => setPage("products")}
              className="bg-blue-700 text-white text-lg px-8 py-4 rounded-2xl shadow-lg"
            >
              Voir les Produits
            </Button>
          </section>

          <section className="bg-blue-50 py-10 text-center">
            <h2 className="text-2xl font-bold text-blue-900 mb-4">Livraison & Paiement</h2>
            <p className="text-gray-700 max-w-3xl mx-auto">
              Nous livrons après réception du paiement. Paiement en main ou en ligne. Le tarif dépend de la distance.
            </p>

            <div className="mt-6 grid md:grid-cols-2 gap-4 max-w-4xl mx-auto text-left">
              <Card className="p-4">
                <h3 className="font-semibold text-blue-800 mb-2">🇩🇴 Santo Domingo</h3>
                <p>Los Girasoles, Calle Rolando Martinez</p>
                <p>📞 WhatsApp / Livraison : +1 (849) 485-5079</p>
                <p>🕓 Horaire : 6h - 21h</p>
              </Card>
              <Card className="p-4">
                <h3 className="font-semibold text-blue-800 mb-2">🇭🇹 Les Cayes</h3>
                <p>67 Lagaudray</p>
                <p>📞 WhatsApp / Livraison : +509 5533 9204</p>
                <p>🕓 Horaire : 6h - 18h</p>
              </Card>
            </div>

            <p className="mt-6 text-gray-700">
              💳 Paiement accepté : MonCash, Caribe Express, Western Union, PayPal
            </p>
            <p className="mt-2 text-gray-700">
              📧 Contact : policardchristian08@gmail.com, jeanfrancenarly811@gmail.com
            </p>
          </section>
        </>
      )}

      {/* Products */}
      {page === "products" && (
        <section className="p-8">
          <h2 className="text-3xl font-bold text-blue-900 text-center mb-8">Nos Produits</h2>
          {Object.keys(products).map((category) => (
            <div key={category} className="mb-12">
              <h3 className="text-2xl font-semibold text-blue-800 mb-4">{category}</h3>
              <div className="grid md:grid-cols-3 gap-6">
                {products[category].map((p) => (
                  <Card key={p.name} className="shadow-md rounded-2xl overflow-hidden border border-gray-100">
                    <img src={p.img} alt={p.name} className="h-48 w-full object-cover" />
                    <CardContent className="p-4 text-center">
                      <h4 className="font-bold text-blue-900 mb-2">{p.name}</h4>
                      <p className="text-gray-600 text-sm mb-4">{p.desc}</p>
                      <Button
                        onClick={() => handleOrder(p.name)}
                        className="bg-green-600 text-white px-4 py-2 rounded-xl"
                      >
                        Commander via WhatsApp
                      </Button>
                    </CardContent>
                  </Card>
                ))}
              </div>
            </div>
          ))}
        </section>
      )}

      <footer className="bg-blue-900 text-white py-4 text-center">
        <p className="text-sm">© 2025 PoliStore — Tous droits réservés</p>
      </footer>
    </div>
  );
}
