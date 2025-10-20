import React, { useState, ChangeEvent, FormEvent } from "react";
import { motion } from "framer-motion";
import { Phone, Mail, MapPin } from "lucide-react";

// Import your local image
import ParlourImg from "../assets/IMG-20251016-WA0007.jpg";

interface Service {
  title: string;
  desc: string;
  price: string;
}

interface Pricing {
  name: string;
  features: string[];
  price: string;
}

export default function SarikaBeauty(): JSX.Element {
  const [name, setName] = useState<string>("");
  const [phone, setPhone] = useState<string>("");
  const [service, setService] = useState<string>("Bridal Makeup");
  const [date, setDate] = useState<string>("");

  const services: Service[] = [
    {
      title: "Bridal Makeup",
      desc: "Full bridal packages, trial sessions, traditional & contemporary looks.",
      price: "From ₹8,000",
    },
    {
      title: "Hair Styling",
      desc: "Cuts, color, blowouts, and special event styling.",
      price: "From ₹800",
    },
    {
      title: "Party Makeup",
      desc: "Quick glam, evening looks, and photoshoot-ready makeup.",
      price: "From ₹1,200",
    },
    {
      title: "Saree & Draping",
      desc: "Traditional draping and pre-bridal styling services.",
      price: "From ₹500",
    },
  ];

  const pricing: Pricing[] = [
    { name: "Basic", features: ["Haircut", "Blowdry"], price: "₹400" },
    {
      name: "Classic",
      features: ["Haircut", "Blowdry", "Basic Makeup"],
      price: "₹1200",
    },
    {
      name: "Bridal",
      features: ["Trial", "Full Makeup", "Hairstyle"],
      price: "From ₹8,000",
    },
  ];

  const handleSubmit = (e: FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    alert(`Thanks ${name}! We received your booking request for ${service} on ${date}.`);
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-white to-slate-50 text-slate-800">
      {/* Header */}
      <header className="max-w-6xl mx-auto px-6 py-6 flex items-center justify-between">
        <div className="flex items-center gap-4">
          <div className="w-12 h-12 bg-pink-500 rounded-full flex items-center justify-center text-white font-bold text-lg shadow-lg">
            SB
          </div>
          <div>
            <h1 className="text-xl font-extrabold">Sarika Beauty</h1>
            <p className="text-sm text-slate-500">Hair & Makeup • Parlour</p>
          </div>
        </div>

        <nav className="hidden md:flex gap-6 items-center text-sm">
          <a href="#services" className="hover:text-pink-500">Services</a>
          <a href="#gallery" className="hover:text-pink-500">Gallery</a>
          <a href="#pricing" className="hover:text-pink-500">Pricing</a>
          <a
            href="#contact"
            className="bg-pink-500 text-white px-4 py-2 rounded-2xl shadow-sm hover:bg-pink-600"
          >
            Book Now
          </a>
        </nav>

        <button className="md:hidden p-2 rounded-md border border-slate-200">
          Menu
        </button>
      </header>

      <main className="max-w-6xl mx-auto px-6">
        {/* HERO */}
        <section className="grid md:grid-cols-2 gap-8 items-center py-12">
          <motion.div
            initial={{ x: -40, opacity: 0 }}
            animate={{ x: 0, opacity: 1 }}
            transition={{ duration: 0.6 }}
          >
            <h2 className="text-4xl md:text-5xl font-extrabold leading-tight">
              Look radiant every day — hair & makeup by Sarika
            </h2>
            <p className="mt-4 text-slate-600 max-w-xl">
              Professional hair styling, bridal makeup, and beauty services that
              make you feel confident. Friendly prices, hygienic workspace, and
              customised looks for every occasion.
            </p>

            <div className="mt-6 flex gap-3">
              <a
                href="#contact"
                className="inline-block bg-pink-500 text-white px-5 py-3 rounded-2xl shadow hover:bg-pink-600"
              >
                Book Appointment
              </a>
              <a
                href="#gallery"
                className="inline-block border border-slate-200 px-5 py-3 rounded-2xl"
              >
                View Gallery
              </a>
            </div>

            <div className="mt-6 flex gap-4 items-center text-sm text-slate-500">
              <div className="flex items-center gap-2">
                <Phone size={16} /> <span>+91 98XXXXXXX</span>
              </div>
              <div className="flex items-center gap-2">
                <MapPin size={16} /> <span>Wardha Rd, Nagpur</span>
              </div>
            </div>
          </motion.div>

          <motion.div
            initial={{ scale: 0.98, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            transition={{ duration: 0.6 }}
            className="rounded-2xl overflow-hidden shadow-2xl"
          >
            <img
              src={ParlourImg}
              alt="Sarika Beauty Parlour"
              className="w-full h-96 object-cover"
            />
          </motion.div>
        </section>

        {/* SERVICES */}
        <section id="services" className="py-8">
          <h3 className="text-2xl font-bold">Our Services</h3>
          <p className="text-slate-600 mt-2">
            From party looks to bridal glam — curated services for every need.
          </p>

          <div className="grid sm:grid-cols-2 lg:grid-cols-4 gap-6 mt-6">
            {services.map((s: Service, i: number) => (
              <motion.div
                key={i}
                whileHover={{ y: -6 }}
                className="p-5 rounded-2xl bg-white shadow-md"
              >
                <h4 className="font-semibold">{s.title}</h4>
                <p className="text-sm text-slate-500 mt-2">{s.desc}</p>
                <div className="mt-4 text-pink-500 font-bold">{s.price}</div>
              </motion.div>
            ))}
          </div>
        </section>

        {/* GALLERY */}
        <section id="gallery" className="py-8">
          <h3 className="text-2xl font-bold">Gallery</h3>
          <p className="text-slate-600 mt-2">
            Glimpses of our happy clients and elegant makeovers.
          </p>

          <div className="grid sm:grid-cols-2 md:grid-cols-3 gap-6 mt-6">
            <motion.img
              whileHover={{ scale: 1.05 }}
              src={ParlourImg}
              alt="Sarika Beauty Work"
              className="rounded-2xl shadow-lg w-full h-80 object-cover"
            />
            <motion.img
              whileHover={{ scale: 1.05 }}
              src="https://images.unsplash.com/photo-1596464716121-3b71b869a4b6?auto=format&fit=crop&w=900&q=60"
              alt="Bridal Look"
              className="rounded-2xl shadow-lg w-full h-80 object-cover"
            />
            <motion.img
              whileHover={{ scale: 1.05 }}
              src="https://images.unsplash.com/photo-1603297631963-5a1a5ff5d5e9?auto=format&fit=crop&w=900&q=60"
              alt="Hair Styling"
              className="rounded-2xl shadow-lg w-full h-80 object-cover"
            />
          </div>
        </section>

        {/* PRICING */}
        <section id="pricing" className="py-8">
          <h3 className="text-2xl font-bold">Pricing</h3>
          <p className="text-slate-600 mt-2">Transparent prices — no surprises.</p>

          <div className="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 mt-6">
            {pricing.map((p: Pricing, idx: number) => (
              <motion.div
                key={idx}
                whileHover={{ scale: 1.02 }}
                className="p-6 rounded-2xl bg-white shadow-md"
              >
                <h4 className="font-bold text-lg">{p.name}</h4>
                <div className="mt-3 text-slate-500 text-sm">
                  {p.features.map((f: string, i: number) => (
                    <div key={i}>• {f}</div>
                  ))}
                </div>
                <div className="mt-4 text-2xl font-extrabold">{p.price}</div>
                <a
                  href="#contact"
                  className="mt-4 inline-block bg-pink-500 text-white px-4 py-2 rounded-lg"
                >
                  Book Now
                </a>
              </motion.div>
            ))}
          </div>
        </section>

        {/* CONTACT */}
        <section id="contact" className="py-12">
          <div className="grid md:grid-cols-2 gap-8 items-start">
            <div>
              <h3 className="text-2xl font-bold">Contact & Booking</h3>
              <p className="text-slate-600 mt-2">
                Call, message or fill the form to book your appointment.
              </p>

              <div className="mt-6 space-y-4 text-sm text-slate-700">
                <div className="flex items-center gap-3">
                  <Phone size={18} />{" "}
                  <div>
                    <strong>Phone:</strong> +91 98XXXXXXX
                  </div>
                </div>
                <div className="flex items-center gap-3">
                  <Mail size={18} />{" "}
                  <div>
                    <strong>Email:</strong> contact@sarikabeauty.com
                  </div>
                </div>
                <div className="flex items-center gap-3">
                  <MapPin size={18} />{" "}
                  <div>
                    <strong>Address:</strong> Wardha Rd, Nagpur
                  </div>
                </div>
              </div>
            </div>

            <div className="bg-white p-6 rounded-2xl shadow-md">
              <form onSubmit={handleSubmit}>
                <div className="mb-3">
                  <label className="block text-sm font-medium">Name</label>
                  <input
                    type="text"
                    value={name}
                    onChange={(e: ChangeEvent<HTMLInputElement>) =>
                      setName(e.target.value)
                    }
                    required
                    className="mt-1 w-full border border-slate-200 rounded-lg px-3 py-2"
                  />
                </div>
                <div className="mb-3">
                  <label className="block text-sm font-medium">Phone</label>
                  <input
                    type="tel"
                    value={phone}
                    onChange={(e: ChangeEvent<HTMLInputElement>) =>
                      setPhone(e.target.value)
                    }
                    required
                    className="mt-1 w-full border border-slate-200 rounded-lg px-3 py-2"
                  />
                </div>
                <div className="mb-3">
                  <label className="block text-sm font-medium">
                    Select Service
                  </label>
                  <select
                    value={service}
                    onChange={(e: ChangeEvent<HTMLSelectElement>) =>
                      setService(e.target.value)
                    }
                    className="mt-1 w-full border border-slate-200 rounded-lg px-3 py-2"
                  >
                    {services.map((s: Service, i: number) => (
                      <option key={i} value={s.title}>
                        {s.title}
                      </option>
                    ))}
                  </select>
                </div>
                <div className="mb-3">
                  <label className="block text-sm font-medium">Date</label>
                  <input
                    type="date"
                    value={date}
                    onChange={(e: ChangeEvent<HTMLInputElement>) =>
                      setDate(e.target.value)
                    }
                    required
                    className="mt-1 w-full border border-slate-200 rounded-lg px-3 py-2"
                  />
                </div>
                <button
                  type="submit"
                  className="bg-pink-500 text-white px-4 py-2 rounded-lg mt-3"
                >
                  Submit
                </button>
              </form>
            </div>
          </div>
        </section>
      </main>
    </div>
  );
}
