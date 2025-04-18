# timeblitz-website
 "Website for TimeBlitz watches"
import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Sparkles, ShoppingCart, Clock, Search, User } from "lucide-react";
import { motion } from "framer-motion";

const watches = [
  { name: "Blitz Classic", price: 2499, img: "https://burst.shopifycdn.com/photos/wooden-watch.jpg?width=1000&format=pjpg&exif=0&iptc=0", tag: "New" },
  { name: "TimeStriker Pro", price: 3999, img: "https://media.gettyimages.com/id/165853320/photo/wristwatch.jpg?s=612x612&w=0&k=20&c=DgQbRd67gNDR0rdOpywkHDTBzLB3ahw_CsMPANtWyY8=" },
  { name: "Elegant Chrono", price: 5499, img: "https://t4.ftcdn.net/jpg/10/07/84/11/360_F_1007841175_1Qs8QVhJdKgToVKaMg0a2HhFmJHjwzOo.jpg" },
  { name: "Ocean Blue", price: 2999, img: "https://img.freepik.com/premium-photo/close-up-wristwatch-box-table_1048944-18217294.jpg?semt=ais_hybrid" },
  { name: "Vintage Luxe", price: 4499, img: "https://media.gettyimages.com/id/171585393/photo/watch.jpg?s=612x612&w=0&k=20&c=eyRhDVc9inHnF2lk7VSE5voUZSNvC6WQalCHhfEwrCY=" },
  { name: "Silver Edge", price: 3199, img: "https://img.freepik.com/free-photo/closeup-shot-modern-cool-black-digital-watch-with-brown-leather-strap_181624-3545.jpg?semt=ais_hybrid&w=740" },
  { name: "Royal Gold", price: 6299, img: "https://media.gettyimages.com/id/172863148/photo/wrist-watch-lying-beautiful-reflection.jpg?s=612x612&w=0&k=20&c=_y_CHVkSbhjbxiUycOYt12M71JcTimG3FkN9L5nFppM=" },
  { name: "Bold Matte", price: 3899, img: "https://img.freepik.com/premium-photo/closeup-luxury-men-s-watch_53876-155400.jpg?semt=ais_hybrid&w=740" },
  { name: "Deep Diver", price: 4999, img: "https://img.freepik.com/premium-photo/gorgeous-luxury-wrist-watch-background_1262174-662.jpg?semt=ais_hybrid" }
];

export default function TimeBlitz() {
  const [filter, setFilter] = useState("All");

  const filtered = watches.filter(w => {
    if (filter === "Affordable") return w.price < 3000;
    if (filter === "Premium") return w.price > 5000;
    return true;
  });

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 text-gray-100 font-sans">
      {/* NavBar */}
      <nav className="flex items-center justify-between p-6 border-b border-gray-700 bg-gray-800 shadow-md sticky top-0 z-50">
        <div className="flex items-center gap-2 text-gray-300 text-2xl font-bold">
          <Clock className="w-6 h-6 text-gray-300" /> TimeBlitz
        </div>
        <div className="flex gap-6 items-center text-sm text-gray-400">
          <button onClick={() => setFilter("All")} className="hover:text-gray-200">Home</button>
          <button onClick={() => setFilter("Affordable")} className="hover:text-gray-200">Affordable</button>
          <button onClick={() => setFilter("Premium")} className="hover:text-gray-200">Premium</button>
          <Search className="w-5 h-5 hover:text-gray-200 cursor-pointer" />
          <ShoppingCart className="w-5 h-5 hover:text-gray-200 cursor-pointer" />
          <User className="w-5 h-5 hover:text-gray-200 cursor-pointer" />
        </div>
      </nav>

      {/* Advertise - Featured Watches */}
      <section className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 px-6 py-16 bg-gray-800">
        <h2 className="col-span-full text-2xl font-bold text-gray-200 text-center mb-6">Featured Offers</h2>
        {watches.slice(0, 3).map((watch, idx) => (
          <motion.div key={idx} whileHover={{ scale: 1.03 }} className="transition-transform">
            <Card className="bg-gray-700 rounded-2xl shadow-lg overflow-hidden border border-gray-600">
              <img src={watch.img} alt={watch.name} className="w-full h-48 object-cover rounded-t-xl" />
              <CardContent className="p-4 text-center">
                <h3 className="text-lg font-semibold text-gray-200">{watch.name}</h3>
                <p className="text-sm text-gray-400 mt-1">₹{watch.price.toLocaleString()}</p>
                <Button className="mt-4 w-full bg-gray-600 text-white hover:bg-gray-500">
                  <ShoppingCart className="mr-2 h-4 w-4" /> Buy Now
                </Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </section>

      {/* Hero */}
      <section className="text-center py-16 px-4">
        <motion.h1
          initial={{ opacity: 0, y: -40 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.8 }}
          className="text-5xl font-extrabold text-gray-200"
        >
          Elevate Your Style
        </motion.h1>
        <p className="mt-4 text-gray-400 max-w-xl mx-auto">
          Discover exclusive timepieces that blend precision, craftsmanship, and timeless elegance.
        </p>
      </section>

      {/* Products */}
      <main className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8 px-6 pb-16">
        {filtered.map((watch, i) => (
          <motion.div key={i} whileHover={{ scale: 1.03 }} className="transition-transform">
            <Card className="bg-gray-800 rounded-2xl shadow-lg overflow-hidden border border-gray-600">
              {watch.tag && (
                <span className="absolute top-3 left-3 bg-gray-600 text-white text-xs px-2 py-1 rounded-full">
                  {watch.tag}
                </span>
              )}
              <img src={watch.img} alt={watch.name} className="w-full h-48 object-cover rounded-t-xl" />
              <CardContent className="p-4 text-center">
                <h2 className="text-lg font-semibold text-gray-200 truncate">{watch.name}</h2>
                <p className="text-sm text-gray-400 mt-1">₹{watch.price.toLocaleString()}</p>
                <Button className="mt-4 w-full bg-gray-600 text-white hover:bg-gray-500">
                  <ShoppingCart className="mr-2 h-4 w-4" /> Buy Now
                </Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </main>

      {/* Footer */}
      <footer className="text-center py-6 border-t border-gray-700 bg-gray-800 text-sm text-gray-400">
        <p className="flex justify-center items-center gap-2">
          <Sparkles className="w-4 h-4 text-gray-200" /> Crafted with passion by TimeBlitz
        </p>
        <p className="mt-2">&copy; {new Date().getFullYear()} TimeBlitz. All rights reserved.</p>
      </footer>
    </div>
  );
}
