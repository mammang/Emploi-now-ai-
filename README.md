
const config = {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};

export default config;

{
  "name": "emploi-now-ai",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint ."
  },
  "dependencies": {
    "next": "^15.5.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "lucide-react": "^0.468.0"
  },
  "devDependencies": {
    "typescript": "^5.7.0",
    "@types/node": "^22.0.0",
    "@types/react": "^19.0.0",
    "eslint": "^9.0.0",
    "eslint-config-next": "^15.5.0",
    "tailwindcss": "^4.0.0",
    "@tailwindcss/postcss": "^4.0.0",
    "postcss": "^8.5.0"
  }
}
# Emploi-now-ai-
Plateforme intelligente de recherche d'emploi internationale avec intelligence artificielle.
# EMPLOI NOW AI

Plateforme internationale intelligente
de recherche d'emploi.

## Objectifs

- Rechercher des emplois dans plusieurs pays.
- Collecter les offres avec Adzuna.
- Connecter les API partenaires.
- Utiliser l'intelligence artificielle.
- Proposer des recommandations personnalisées.

## Technologies

- Frontend : Next.js
- Backend : Supabase
- Intelligence artificielle : AI API
{
  "name": "emploi-now-ai",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint ."
  },
  "dependencies": {
    "next": "^15.5.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "lucide-react": "^0.468.0"
  },
  "devDependencies": {
    "typescript": "^5.7.0",
    "@types/node": "^22.0.0",
    "@types/react": "^19.0.0",
    "eslint": "^9.0.0",
    "eslint-config-next": "^15.5.0"
  }
}

"use client";

import { useState } from "react";
import {
  Search,
  MapPin,
  Briefcase,
  Globe,
  Bot,
  ArrowRight,
  Building2,
  Sparkles,
  Menu,
} from "lucide-react";

const jobs = [
  {
    title: "Développeur Web",
    company: "Entreprise technologique",
    location: "Paris, France",
    type: "Temps plein",
    category: "Technologie",
  },
  {
    title: "Assistant administratif",
    company: "Entreprise internationale",
    location: "Berlin, Allemagne",
    type: "Temps plein",
    category: "Administration",
  },
  {
    title: "Responsable Marketing",
    company: "Agence de communication",
    location: "Douala, Cameroun",
    type: "Hybride",
    category: "Marketing",
  },
];

export default function Home() {
  const [keyword, setKeyword] = useState("");
  const [country, setCountry] = useState("");
  const [searched, setSearched] = useState(false);

  const filteredJobs = jobs.filter((job) => {
    const matchesKeyword =
      `${job.title} ${job.company} ${job.category}`
        .toLowerCase()
        .includes(keyword.toLowerCase());

    const matchesCountry =
      job.location.toLowerCase().includes(country.toLowerCase());

    return matchesKeyword && matchesCountry;
  });

  return (
    <main className="min-h-screen bg-slate-50 text-slate-900">
      <header className="bg-white border-b">
        <nav className="max-w-7xl mx-auto px-6 py-5 flex justify-between items-center">
          <a href="/" className="text-2xl font-black text-blue-700">
            EMPLOI NOW <span className="text-orange-500">AI</span>
          </a>

          <div className="hidden md:flex gap-8 items-center">
            <a href="#accueil">Accueil</a>
            <a href="#emplois">Offres d'emploi</a>
            <a href="#apropos">À propos</a>
          </div>

          <button className="bg-blue-700 text-white px-5 py-3 rounded-xl">
            Espace candidat
          </button>
        </nav>
      </header>

      <section id="accueil" className="bg-blue-950 text-white py-24 px-6">
        <div className="max-w-5xl mx-auto text-center">
          <div className="inline-flex items-center gap-2 bg-blue-900 px-4 py-2 rounded-full mb-6">
            <Sparkles size={18} />
            L'emploi intelligent et international
          </div>

          <h1 className="text-4xl md:text-6xl font-black leading-tight">
            Le monde du travail
            <span className="text-orange-400"> à portée de main.</span>
          </h1>

          <p className="text-blue-100 text-lg mt-6 max-w-2xl mx-auto">
            Trouvez des opportunités professionnelles dans
            plusieurs pays grâce à l'intelligence artificielle.
          </p>

          <form
            className="bg-white rounded-2xl p-3 mt-10 flex flex-col md:flex-row gap-3"
            onSubmit={(event) => {
              event.preventDefault();
              setSearched(true);
              document.getElementById("emplois")?.scrollIntoView({
                behavior: "smooth",
              });
            }}
          >
            <div className="flex items-center gap-3 flex-1 px-3">
              <Search className="text-blue-700" />
              <input
                value={keyword}
                onChange={(event) => setKeyword(event.target.value)}
                placeholder="Métier, compétence..."
                className="w-full text-slate-900 outline-none py-3"
              />
            </div>

            <div className="flex items-center gap-3 flex-1 px-3">
              <MapPin className="text-blue-700" />
              <input
                value={country}
                onChange={(event) => setCountry(event.target.value)}
                placeholder="Ville ou pays"
                className="w-full text-slate-900 outline-none py-3"
              />
            </div>

            <button className="bg-orange-500 hover:bg-orange-600 text-white font-bold px-8 py-4 rounded-xl">
              Rechercher
            </button>
          </form>

          <p className="text-blue-200 mt-5 text-sm">
            France · Allemagne · Cameroun · Canada · Monde entier
          </p>
        </div>
      </section>

      <section className="max-w-7xl mx-auto px-6 py-16">
        <div className="grid md:grid-cols-3 gap-6">
          {[
            { icon: Globe, title: "International", desc: "Explorez plusieurs pays." },
            { icon: Bot, title: "Intelligence artificielle", desc: "Préparez votre recherche d'emploi." },
            { icon: Briefcase, title: "Opportunités", desc: "Découvrez différents métiers." },
          ].map((item) => (
            <div key={item.title} className="bg-white p-7 rounded-2xl shadow-sm">
              <item.icon size={32} className="text-blue-700 mb-4" />
              <h2 className="font-bold text-xl">{item.title}</h2>
              <p className="text-slate-500 mt-2">{item.desc}</p>
            </div>
          ))}
        </div>
      </section>

      <section id="emplois" className="max-w-7xl mx-auto px-6 pb-20">
        <div className="flex justify-between items-center mb-8">
          <div>
            <p className="text-blue-700 font-bold">OPPORTUNITÉS</p>
            <h2 className="text-3xl font-black mt-2">
              Découvrez les emplois
            </h2>
          </div>
          <Building2 className="text-blue-700" size={35} />
        </div>

        {searched && (
          <p className="mb-5 text-slate-600">
            {filteredJobs.length} résultat(s) dans les exemples de démonstration.
          </p>
        )}

        <div className="grid md:grid-cols-3 gap-6">
          {filteredJobs.map((job) => (
            <article key={job.title} className="bg-white p-6 rounded-2xl border shadow-sm">
              <div className="bg-blue-50 w-12 h-12 rounded-xl flex items-center justify-center">
                <Briefcase className="text-blue-700" />
              </div>

              <h3 className="text-xl font-bold mt-5">{job.title}</h3>
              <p className="text-slate-500 mt-2">{job.company}</p>

              <div className="flex items-center gap-2 mt-5 text-slate-600">
                <MapPin size={17} />
                {job.location}
              </div>

              <div className="flex justify-between items-center mt-6">
                <span className="bg-blue-50 text-blue-700 px-3 py-2 rounded-lg text-sm">
                  {job.type}
                </span>
                <ArrowRight className="text-blue-700" />
              </div>

              <p className="text-xs text-orange-600 mt-4">
                Exemple de démonstration
              </p>
            </article>
          ))}
        </div>

        {filteredJobs.length === 0 && (
          <p className="text-slate-500 mt-6">
            Aucun exemple ne correspond à cette recherche.
          </p>
        )}
      </section>

      <section id="apropos" className="bg-blue-950 text-white py-14 px-6 text-center">
        <Bot size={40} className="mx-auto text-orange-400" />
        <h2 className="text-3xl font-black mt-4">
          EMPLOI NOW AI
        </h2>
        <p className="text-blue-200 mt-3">
          Votre avenir professionnel commence ici.
        </p>
      </section>

      <footer className="bg-white text-center p-6 text-slate-500 text-sm">
        © 2026 EMPLOI NOW AI - Tous droits réservés.
      </footer>
    </main>
  );
}

import type { Metadata } from "next";
import "./globals.css";

export const metadata: Metadata = {
  title: "EMPLOI NOW AI | Emploi international",
  description:
    "Trouvez des opportunités professionnelles partout dans le monde grâce à EMPLOI NOW AI.",
  applicationName: "EMPLOI NOW AI",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="fr">
      <body>
        {children}
      </body>
    </html>
  );
}

import type { Metadata } from "next";
import "./globals.css";

export const metadata: Metadata = {
  title: "EMPLOI NOW AI | Emploi international",
  description:
    "Trouvez des opportunités professionnelles partout dans le monde grâce à EMPLOI NOW AI.",
  applicationName: "EMPLOI NOW AI",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="fr">
      <body>
        {children}
      </body>
    </html>
  );
}
@import "tailwindcss";

:root {
  --background: #f8fafc;
  --foreground: #0f172a;
  --primary: #1d4ed8;
  --secondary: #f97316;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0;
  background: var(--background);
  color: var(--foreground);
  font-family: Arial, Helvetica, sans-serif;
}

button,
input {
  font: inherit;
}

button {
  cursor: pointer;
}

a {
  text-decoration: none;
}

::selection {
  background: #bfdbfe;
  color: #1e3a8a;
}

@import "tailwindcss";

:root {
  --background: #f8fafc;
  --foreground: #0f172a;
  --primary: #1d4ed8;
  --secondary: #f97316;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0;
  background: var(--background);
  color: var(--foreground);
  font-family: Arial, Helvetica, sans-serif;
}

button,
input {
  font: inherit;
}

button {
  cursor: pointer;
}

a {
  text-decoration: none;
}

::selection {
  background: #bfdbfe;
  color: #1e3a8a;
}

@import "tailwindcss";

:root {
  --background: #f8fafc;
  --foreground: #0f172a;
  --primary: #1d4ed8;
  --secondary: #f97316;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0;
  background: var(--background);
  color: var(--foreground);
  font-family: Arial, Helvetica, sans-serif;
}

button,
input {
  font: inherit;
}

button {
  cursor: pointer;
}

a {
  text-decoration: none;
}

::selection {
  background: #bfdbfe;
  color: #1e3a8a;
}

