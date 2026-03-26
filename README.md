import React, { useState } from 'react';
import { 
  Menu, 
  X, 
  Anchor, 
  CalendarDays, 
  MapPin, 
  Mail, 
  Users, 
  Navigation,
  ChevronRight,
  BookOpen,
  Award,
  Wrench,
  PenTool,
  PiggyBank,
  Shield,
  Map,
  ExternalLink,
  Download,
  Upload,
  Image as ImageIcon,
  MessageSquare,
  Home
} from 'lucide-react';

// Das SRV Logo (Gekreuzte Ruder)
const SrvLogo = ({ className }) => (
  <svg viewBox="0 0 400 300" className={className} xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
        <feDropShadow dx="2" dy="4" stdDeviation="3" floodOpacity="0.6" floodColor="#000000" />
      </filter>
    </defs>
    
    <line x1="100" y1="240" x2="280" y2="60" stroke="#111" strokeWidth="12" strokeLinecap="round" filter="url(#shadow)" />
    <path d="M 275 65 L 305 20 Q 330 30 335 55 L 290 95 Z" fill="#ffffff" stroke="#e0e0e0" strokeWidth="2" filter="url(#shadow)" />

    <line x1="300" y1="240" x2="120" y2="60" stroke="#111" strokeWidth="12" strokeLinecap="round" filter="url(#shadow)" />
    <path d="M 125 65 L 95 20 Q 70 30 65 55 L 110 95 Z" fill="#ffffff" stroke="#e0e0e0" strokeWidth="2" filter="url(#shadow)" />

    <text x="200" y="170" fontFamily="'Comic Sans MS', 'Chalkboard SE', 'Marker Felt', sans-serif" fontSize="130" fill="#ffffff" textAnchor="middle" filter="url(#shadow)">SRV</text>
    
    <text x="200" y="240" fontFamily="'Comic Sans MS', 'Chalkboard SE', 'Marker Felt', sans-serif" fontSize="26" fill="#ffffff" textAnchor="middle" filter="url(#shadow)">ERNST-KALKUHL GYMNASIUM</text>
    <text x="200" y="275" fontFamily="'Comic Sans MS', 'Chalkboard SE', 'Marker Felt', sans-serif" fontSize="28" fill="#ffffff" textAnchor="middle" filter="url(#shadow)">BONN</text>
  </svg>
);

export default function App() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [currentPage, setCurrentPage] = useState('home');

  const toggleMenu = () => setIsMenuOpen(!isMenuOpen);

  const navigateTo = (page) => {
    setCurrentPage(page);
    setIsMenuOpen(false);
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  const navLinks = [
    { id: 'home', label: 'Startseite' },
    { id: 'aktuelles', label: 'Aktuelles & Fotos' },
    { id: 'about', label: 'Über uns & Bootshaus' },
    { id: 'vorstand', label: 'Vorstand' },
    { id: 'fleet', label: 'Flotte' },
    { id: 'events', label: 'Termine' },
    { id: 'contact', label: 'Kontakt' }
  ];

  // --- DATEN ---
  const termine2026 = [
    { date: "Ab sofort", title: "Winteraktivitäten", desc: "Bootsarbeiten, Steuermannskurs Theorie (mit ARC), DLRG und weitere Termine nach Ankündigung." },
    { date: "16.03. - 20.03.", title: "Anfängerwerbung", desc: "Werbung für den SRV in den 6. Klassen." },
    { date: "Mo, 23.03.", title: "Anmeldung Anfängerwochenende", desc: "Interessenten aus höheren Klassen können bei freien Kapazitäten hinzukommen." },
    { date: "Fr, 17.04. - So, 19.04.", title: "Anfängerwochenende", desc: "Auf dem südlichen Rheinauensee. Grillen, Sonne und Booteputzen am Sonntag." },
    { date: "Ab 06. April", title: "Ruderausbildung", desc: "Mittwochs und Freitags. Elternabend folgt." },
    { date: "Fr, 01.05.", title: "50 Jahre SRV!", desc: "Großes Jubiläum! Feier im Bootshaus, genaue Infos folgen." },
    { date: "Sa, 02.05.", title: "Eurega", desc: "Langstreckenregatta Neuwied-Bonn (45km) oder St. Goar-Bonn (100km)." },
    { date: "13.05. - 17.05.", title: "Lahnwanderfahrt", desc: "Über Himmelfahrt. Von Diez nach Bonn (Zelte & Bootshaus Neuwied)." },
    { date: "So, 24.05.", title: "Vogalonga (Venedig)", desc: "In und um Venedig (Ausnahme-Auslandstour). Teilnahme ab 16." },
    { date: "Sommer", title: "Regatten & Wanderfahrt", desc: "Schülerregatta, Jtfo und Sommerwanderfahrt 2026." },
    { date: "30.09. - 04.10.", title: "Herbstwanderfahrt", desc: "Termin 'Rund um den 3. Oktober'." },
    { date: "So, 01.11.", title: "Allerheiligenfahrt", desc: "30km Tagestour von Bonn nach Köln." },
    { date: "Fr, 27.11.", title: "Jahreshauptversammlung", desc: "Jahreshauptversammlung des Vereins." }
  ];

  const vorstand = [
    { role: "Präsident", names: "Florian Kurth", desc: "Repräsentiert den Verein und koordiniert die Vorstandsarbeit.", icon: <Award className="h-8 w-8 text-green-700" /> },
    { role: "Ruderwarte", names: "Florian Kurth & Julian Klein", desc: "Organisieren den Ruderbetrieb und die Einteilung der Boote.", icon: <Navigation className="h-8 w-8 text-green-700" /> },
    { role: "Wanderwarte", names: "Jannik Breuer & Martha Herden", desc: "Planen die Lahnwanderfahrt, Herbstwanderfahrt und Regatten.", icon: <Map className="h-8 w-8 text-green-700" /> },
    { role: "Bootswarte", names: "Henri Ewert, Justin Nack & Tobias Kuß", desc: "Zuständig für die Instandhaltung unserer Boote.", icon: <Wrench className="h-8 w-8 text-green-700" /> },
    { role: "Schriftwartinnen", names: "Martha Herden & Lilly Keunecke", desc: "Kümmern sich um die Protokolle und Öffentlichkeitsarbeit.", icon: <PenTool className="h-8 w-8 text-green-700" /> },
    { role: "Kassenwartin", names: "Isabelle Hölter", desc: "Verwaltet die Finanzen, Beiträge und Zuschüsse des Vereins.", icon: <PiggyBank className="h-8 w-8 text-green-700" /> },
    { role: "Protektor", names: "Christopher Dahm", desc: "Sportlehrer der Schule, berät den Vorstand und hält die Verbindung zum Kollegium.", icon: <Shield className="h-8 w-8 text-green-700" /> }
  ];

  const newsFeed = [
    { 
      id: 1, 
      date: "Frühjahr 2026", 
      title: "Jubiläumsjahr 2026: 50 Jahre SRV!", 
      content: "In diesem Jahr feiern wir unser 50-jähriges Bestehen! Tragt euch den 1. Mai schon einmal fest in den Kalender ein – genauere Infos zur geplanten Feier im Bootshaus folgen bald.", 
      imagePlaceholder: "" 
    },
    { 
      id: 2, 
      date: "März 2026", 
      title: "Anfängerwerbung & Anfängerwochenende", 
      content: "Die Anfängerwerbung in den 6. Klassen ist in vollem Gange. Wer Lust hat, den Rudersport auszuprobieren, kann sich am 23. März für das Anfängerwochenende am Rheinauensee anmelden. Wir freuen uns auf euch!" 
    },
    { 
      id: 3, 
      date: "Winter/Frühjahr 2026", 
      title: "Laufende Winteraktivitäten", 
      content: "Unsere winterlichen Bootsarbeiten laufen auf Hochtouren, damit die Flotte rechtzeitig zur neuen Saison wieder in Topform ist. Denkt bitte auch an den theoretischen Steuermannskurs in Kooperation mit dem ARC." 
    }
  ];

  // --- SEITEN-KOMPONENTEN ---
  const renderHome = () => (
    <div className="animate-fadeIn">
      <section className="relative pt-24 pb-16 md:pt-40 md:pb-32 overflow-hidden min-h-[85vh] flex items-center bg-gray-900">
        
        {/* Background Image / Placeholder */}
        <div className="absolute inset-0 z-0">
          {/* Ein dekoratives Hintergrundbild, das einen Fluss simuliert, überlagert vom geforderten Placeholder-Text */}
          <img 
            src="https://images.unsplash.com/photo-1549474086-4b80bba3b5d2?q=80&w=2000&auto=format&fit=crop" 
            alt="Rhein Panorama" 
            className="w-full h-full object-cover"
          />
          <div className="absolute inset-0 bg-green-950/80 mix-blend-multiply z-10"></div> 
          
          <div className="absolute inset-0 z-20 flex items-center justify-center opacity-40 pointer-events-none">
            <span className="text-white text-3xl font-bold uppercase tracking-widest border-2 border-white/50 p-6 rounded-lg backdrop-blur-sm">
              
            </span>
          </div>
        </div>

        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-30 w-full">
          <div className="inline-block mb-6 px-5 py-2 bg-green-600/40 text-green-50 border border-green-400/50 rounded-full font-bold text-sm tracking-widest shadow-lg backdrop-blur-md uppercase">
            Jubiläumsjahr 2026: 50 Jahre SRV
          </div>
          <h1 className="text-5xl md:text-7xl lg:text-8xl font-extrabold text-white tracking-tight mb-6 drop-shadow-xl">
            Rudersport aus <span className="text-transparent bg-clip-text bg-gradient-to-r from-green-400 to-green-200">Tradition.</span>
          </h1>
          <p className="mt-6 text-xl md:text-2xl text-green-50/90 max-w-3xl mx-auto mb-10 leading-relaxed drop-shadow-md">
            Willkommen beim Schüler-Ruder-Verein am Ernst-Kalkuhl-Gymnasium. Seit 1976 rudern wir selbstständig auf dem Rhein und auf vielen Gewässern Deutschlands.
          </p>
          <div className="flex justify-center gap-5 flex-wrap">
            <button 
              onClick={() => navigateTo('aktuelles')}
              className="bg-green-600 text-white px-8 py-4 rounded-full font-bold text-lg hover:bg-green-500 transition-all shadow-xl hover:shadow-2xl flex items-center transform hover:-translate-y-1"
            >
              Aktuelles & Fotos <ChevronRight className="ml-2 h-5 w-5" />
            </button>
            <button 
              onClick={() => navigateTo('about')}
              className="bg-white/10 backdrop-blur-sm text-white border-2 border-white/80 px-8 py-4 rounded-full font-bold text-lg hover:bg-white/20 transition-all shadow-lg flex items-center transform hover:-translate-y-1"
            >
              Über unseren Verein
            </button>
          </div>
        </div>
      </section>
    </div>
  );

  const renderAktuelles = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl md:text-4xl font-extrabold text-green-900 mb-4 flex items-center justify-center">
            <MessageSquare className="mr-3 h-8 w-8 text-green-600" /> Aktuelles & Galerie
          </h2>
          <p className="text-gray-600 text-lg max-w-2xl mx-auto">
            Neuigkeiten, anstehende Termine und Fotos unserer Mitglieder.
          </p>
        </div>

        <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
          {/* Main Feed */}
          <div className="lg:col-span-2 space-y-8">
            {newsFeed.map(news => (
              <div key={news.id} className="bg-white p-6 rounded-2xl shadow-sm border border-gray-100">
                <div className="flex justify-between items-start mb-4">
                  <h3 className="text-xl font-bold text-gray-900">{news.title}</h3>
                  <span className="text-sm font-medium text-green-700 bg-green-50 px-3 py-1 rounded-full">{news.date}</span>
                </div>
                <p className="text-gray-600 mb-4">{news.content}</p>
                {news.imagePlaceholder && (
                  <div className="w-full h-64 bg-gray-100 rounded-xl flex items-center justify-center border border-gray-200 overflow-hidden">
                    <div className="text-center text-gray-500 font-medium px-4">
                      <ImageIcon className="h-10 w-10 mx-auto mb-3 text-gray-400" />
                      {news.imagePlaceholder}
                    </div>
                  </div>
                )}
              </div>
            ))}
          </div>

          {/* Sidebar / Upload Area & Downloads */}
          <div className="space-y-8">
            {/* Upload Widget */}
            <div className="bg-green-50 p-6 rounded-2xl border border-green-200">
              <h3 className="text-lg font-bold text-green-900 mb-2 flex items-center">
                <Upload className="mr-2 h-5 w-5" /> Fotos hochladen
              </h3>
              <p className="text-sm text-gray-600 mb-4">
                Warst du auf einer Wanderfahrt oder Regatta? Lade hier deine Bilder hoch (nur für eingeloggte Mitglieder).
              </p>
              <div className="border-2 border-dashed border-green-300 rounded-xl p-8 text-center bg-white hover:bg-green-50 transition-colors cursor-pointer">
                <ImageIcon className="h-8 w-8 mx-auto text-green-500 mb-2" />
                <span className="text-sm font-medium text-green-800">Klicke hier oder ziehe Bilder hinein</span>
              </div>
              <button className="w-full mt-4 bg-green-700 text-white py-2 rounded-lg font-medium hover:bg-green-600 transition-colors opacity-50 cursor-not-allowed">
                Hochladen (Login erforderlich)
              </button>
            </div>

            {/* SRV Aktuell Downloads */}
            <div className="bg-white p-6 rounded-2xl shadow-sm border border-gray-100">
              <h3 className="text-lg font-bold text-gray-900 mb-4 flex items-center">
                <BookOpen className="mr-2 h-5 w-5 text-green-600" /> SRV-Aktuell Magazin
              </h3>
              <p className="text-sm text-gray-600 mb-4">
                Einmal im Jahr erscheint unsere Vereinspublikation mit Fahrtenberichten und Neuigkeiten. Hier könnt ihr die letzten Ausgaben herunterladen:
              </p>
              <ul className="space-y-3">
                <li>
                  <a href="https://kalkuhl.de/vereine/ruderverein/" target="_blank" rel="noopener noreferrer" className="flex items-center text-green-700 hover:text-green-900 font-medium group text-sm">
                    <Download className="mr-2 h-4 w-4 text-gray-400 group-hover:text-green-600" /> Ausgabe 2024
                  </a>
                </li>
                <li>
                  <a href="https://kalkuhl.de/vereine/ruderverein/" target="_blank" rel="noopener noreferrer" className="flex items-center text-green-700 hover:text-green-900 font-medium group text-sm">
                    <Download className="mr-2 h-4 w-4 text-gray-400 group-hover:text-green-600" /> Ausgabe 2023
                  </a>
                </li>
                <li className="pt-2 mt-2 border-t border-gray-100">
                  <a href="https://kalkuhl.de/vereine/ruderverein/" target="_blank" rel="noopener noreferrer" className="text-xs text-gray-500 hover:text-green-700 flex items-center">
                    Alle Ausgaben auf Kalkuhl.de ansehen <ExternalLink className="ml-1 h-3 w-3" />
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  );

  const renderAbout = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        
        {/* Geschichte */}
        <div className="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-20 items-center mb-20">
          <div>
            <h2 className="text-3xl font-extrabold text-green-900 mb-6 flex items-center">
              <Users className="mr-4 text-green-600 h-8 w-8" /> Vereinsgeschichte
            </h2>
            <div className="prose prose-lg text-gray-600">
              <p>
                Der Rudersport hat eine lange Tradition am Ernst Kalkuhl Gymnasium (EKG). Schon 1922 wurde der „Ruderclub Kalkuhl“ gegründet. Seit dem 1. Mai 1976 wird diese Tradition mit dem Schüler-Ruder-Verein (SRV) fortgesetzt.
              </p>
              <p>
                Im SRV haben Jugendliche die Chance, nicht nur einen attraktiven Sport kennenzulernen, sondern erfahren auch kameradschaftliches Verhalten. Die Schüler wählen aus ihrer Mitte einen Vorstand, der <strong>vollkommen selbständig</strong> das Vereinsleben organisiert. Lediglich beratend wirkt der Protektor, ein Sportlehrer der Schule.
              </p>
              <p>
                Mit ca. 45 Mitgliedern widmen wir uns vor allem dem Breitensport und Wanderfahrten auf dem Rhein und auf vielen anderen Flüssen Deutschlands (wie z.B. bei der alljährlichen Lahnfahrt an Himmelfahrt).
              </p>
            </div>
          </div>
          <div className="relative h-full flex items-center">
            <div className="bg-gradient-to-br from-green-800 to-green-950 rounded-3xl p-8 w-full flex flex-col items-center justify-center min-h-[350px] shadow-2xl border border-green-700">
               <SrvLogo className="h-48 w-64 mb-6 drop-shadow-2xl" />
            </div>
          </div>
        </div>

        {/* Bootshaus */}
        <div className="bg-gray-50 rounded-3xl p-8 md:p-12 border border-gray-200">
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
            <div className="order-2 lg:order-1 relative">
               <div className="w-full h-64 md:h-80 bg-white rounded-2xl flex items-center justify-center border border-gray-300 shadow-sm overflow-hidden bg-[url('https://www.transparenttextures.com/patterns/diagmonds-light.png')]">
                 <div className="text-center p-6 bg-white/90 backdrop-blur-sm rounded-xl border border-gray-200 shadow-sm mx-4">
                   <Home className="h-12 w-12 mx-auto mb-3 text-green-700" />
                   <p className="font-bold text-gray-800 text-lg"></p>
                 </div>
               </div>
            </div>
            <div className="order-1 lg:order-2">
              <h2 className="text-3xl font-extrabold text-green-900 mb-6">
                Unser Bootshaus
              </h2>
              <p className="text-lg text-gray-600 mb-4 leading-relaxed">
                Der zentrale Dreh- und Angelpunkt unseres Vereinslebens ist das Bootshaus in der Dahlmannstraße (Bonn-Gronau), in direkter Lage am Stresemannufer des Rheins.
              </p>
              <p className="text-lg text-gray-600 mb-6 leading-relaxed">
                Wir teilen uns das Gebäude partnerschaftlich mit dem Akademischen Ruderclub (ARC) Rhenus Bonn. Hier lagern wir unsere Boote, führen Reparaturen durch und starten unsere regelmäßigen Trainingseinheiten auf dem Wasser.
              </p>
              <ul className="space-y-3">
                <li className="flex items-start"><Anchor className="h-6 w-6 text-green-600 mr-2 flex-shrink-0 mt-0.5" /> <span className="text-gray-700">Direkter Zugang zum Rhein.</span></li>
                <li className="flex items-start"><Wrench className="h-6 w-6 text-green-600 mr-2 flex-shrink-0 mt-0.5" /> <span className="text-gray-700">Werkstatt für unsere gemeinsamen winterlichen Bootsarbeiten.</span></li>
                <li className="flex items-start"><Users className="h-6 w-6 text-green-600 mr-2 flex-shrink-0 mt-0.5" /> <span className="text-gray-700">Gemeinsame Nutzung und Pflege mit dem ARC Rhenus.</span></li>
              </ul>
            </div>
          </div>
        </div>

      </div>
    </div>
  );

  const renderVorstand = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-16">
          <span className="text-green-600 font-bold tracking-wider uppercase text-sm">Saison 2025/2026</span>
          <h2 className="text-3xl md:text-4xl font-extrabold mt-2 mb-4 text-green-900">
            Der Vorstand
          </h2>
          <p className="text-gray-600 text-lg max-w-2xl mx-auto">
            Unser Verein wird maßgeblich von den Schülerinnen und Schülern selbst verwaltet. Unterstützt werden sie dabei vom Protektor der Schule.
          </p>
        </div>

        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
          {vorstand.map((amt, idx) => (
            <div key={idx} className={`bg-gray-50 p-8 rounded-2xl shadow-sm border border-gray-100 flex flex-col items-center text-center hover:shadow-md transition-shadow ${amt.role === 'Präsident' ? 'ring-2 ring-green-600 relative overflow-hidden bg-white' : ''}`}>
              {amt.role === 'Präsident' && <div className="absolute top-0 w-full h-1 bg-green-600"></div>}
              <div className="w-16 h-16 bg-white rounded-2xl flex items-center justify-center mb-5 transform rotate-3 shadow-sm border border-gray-100">
                {amt.icon}
              </div>
              <h3 className="text-xl font-bold text-gray-900 mb-1">{amt.role}</h3>
              <p className="text-green-700 font-bold mb-3">{amt.names}</p>
              <p className="text-gray-600 text-sm leading-relaxed mb-4 flex-grow">
                {amt.desc}
              </p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  const renderFleet = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-16">
          <h2 className="text-3xl md:text-4xl font-extrabold mb-4 text-green-900">Unsere Flotte</h2>
          <p className="text-gray-600 text-lg max-w-2xl mx-auto leading-relaxed">
            In unserem Bootshaus beherbergen wir eine vielfältige Auswahl an Ruderbooten, von robusten Gig-Booten bis zu unseren schnellen Einer-Skiffs.
          </p>
        </div>
        
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-5xl mx-auto">
          {/* Das historische Boot */}
          <div className="bg-green-800 rounded-2xl p-8 border border-green-700 shadow-xl relative overflow-hidden">
            <div className="absolute top-0 right-0 bg-yellow-500 text-yellow-900 text-xs font-bold px-3 py-1 rounded-bl-lg shadow-sm">Historisch</div>
            <h3 className="text-2xl font-bold text-white mb-3 mt-2">Die "Oberkassel"</h3>
            <p className="text-green-200 text-sm mb-6 leading-relaxed">Unser erstes eigenes Boot, das 1978 angeschafft wurde. Ein klassisches Gig-Boot und bis heute fahrbereit!</p>
          </div>
          
          <div className="bg-green-800 rounded-2xl p-8 border border-green-700 shadow-lg flex flex-col justify-between">
            <div>
              <h3 className="text-2xl font-bold text-white mb-3">Gig-Boote</h3>
              <p className="text-green-200 text-sm mb-6 leading-relaxed">Robust und sicher. Perfekt für die Ausbildung, Wanderfahrten auf deutschen Flüssen und Touren auf dem Rhein.</p>
            </div>
            <div className="text-green-400 font-bold text-sm bg-green-950/50 inline-block px-4 py-2 rounded self-start">2x / 3x / 4x</div>
          </div>
          
          <div className="bg-green-800 rounded-2xl p-8 border border-green-700 shadow-lg flex flex-col justify-between">
            <div>
              <h3 className="text-2xl font-bold text-white mb-3">Skiffs & Einer</h3>
              <p className="text-green-200 text-sm mb-6 leading-relaxed">Für individuelle Technikschulung und Skiff-Wochenenden am südlichen Rheinauensee.</p>
            </div>
            <div className="text-green-400 font-bold text-sm bg-green-950/50 inline-block px-4 py-2 rounded self-start">1x</div>
          </div>
        </div>
      </div>
    </div>
  );

  const renderEvents = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-16">
          <h2 className="text-3xl font-extrabold text-green-900 flex items-center justify-center mb-4">
            <CalendarDays className="mr-3 h-8 w-8 text-green-600" /> SRV Termine 2026
          </h2>
          <p className="text-gray-500 max-w-xl mx-auto">
            Alle Angaben unter Vorbehalt. Änderungen werden über die üblichen Kanäle kommuniziert.
          </p>
        </div>

        <div className="relative border-l-4 border-green-100 ml-4 md:ml-6 space-y-10">
          {termine2026.map((termin, index) => (
            <div key={index} className="relative pl-6 md:pl-10">
              <div className="absolute -left-[10px] top-1 h-4 w-4 rounded-full bg-green-600 ring-4 ring-white shadow-sm"></div>
              <div className="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition-shadow">
                <div className="flex flex-col md:flex-row md:justify-between md:items-start mb-3">
                  <h3 className="text-xl font-bold text-gray-900">{termin.title}</h3>
                  <span className="inline-block bg-green-50 text-green-800 font-bold px-4 py-1.5 rounded-full text-sm mt-2 md:mt-0 whitespace-nowrap border border-green-100">
                    {termin.date}
                  </span>
                </div>
                <p className="text-gray-600 leading-relaxed">{termin.desc}</p>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  const renderContact = () => (
    <div className="py-12 md:py-20 animate-fadeIn">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-20">
          <div>
            <span className="text-green-600 font-bold tracking-wider uppercase text-sm">Mitglied werden</span>
            <h2 className="text-3xl font-extrabold text-green-900 mt-2 mb-6">Kontakt zum SRV</h2>
            <p className="text-gray-600 mb-8 text-lg">
              Du bist am Ernst-Kalkuhl-Gymnasium und hast Lust aufs Rudern? Komm zu unserer Anfängerwerbung, melde dich für das Anfängerwochenende an oder sprich einfach unseren Protektor an!
            </p>
            
            <div className="space-y-6 bg-white p-8 rounded-2xl shadow-sm border border-gray-100">
              
              <div className="flex items-start">
                <div className="bg-green-100 p-3 rounded-full mr-5 mt-1 shrink-0">
                  <MapPin className="h-6 w-6 text-green-700" />
                </div>
                <div>
                  <p className="font-bold text-lg text-gray-900 mb-1">Ernst-Kalkuhl-Gymnasium</p>
                  <p className="text-gray-600">Königswinterer Str. 534<br/>53227 Bonn (Oberkassel)</p>
                </div>
              </div>
              
              <div className="w-full h-px bg-gray-100"></div>

              <div className="flex items-start">
                <div className="bg-green-100 p-3 rounded-full mr-5 mt-1 shrink-0">
                  <Home className="h-6 w-6 text-green-700" />
                </div>
                <div>
                  <p className="font-bold text-lg text-gray-900 mb-1">Unser Bootshaus</p>
                  <p className="text-gray-600">Dahlmannstraße 1<br/>53113 Bonn (Gronau)</p>
                </div>
              </div>
              
              <div className="w-full h-px bg-gray-100"></div>
              
              <div className="flex items-start">
                <div className="bg-green-100 p-3 rounded-full mr-5 mt-1 shrink-0">
                  <Mail className="h-6 w-6 text-green-700" />
                </div>
                <div>
                  <p className="font-bold text-lg text-gray-900 mb-1">E-Mail Kontakt</p>
                  <p className="text-gray-600 mb-1">
                    <a href="mailto:SRV@kalkuhl.de" className="text-green-700 font-semibold hover:underline">SRV@kalkuhl.de</a>
                    <span className="text-sm ml-2">(Vorstand)</span>
                  </p>
                  <p className="text-gray-600">
                    <a href="mailto:dahm@kalkuhl.de" className="text-green-700 font-semibold hover:underline">dahm@kalkuhl.de</a>
                    <span className="text-sm ml-2">(Herr Dahm, Protektor)</span>
                  </p>
                </div>
              </div>
            </div>
          </div>

          <div className="bg-white p-8 rounded-2xl border border-gray-100 shadow-xl relative">
            <div className="absolute top-0 left-0 w-full h-2 bg-green-700 rounded-t-2xl"></div>
            <h3 className="text-2xl font-bold text-gray-900 mb-6">Nachricht schreiben</h3>
            <form className="space-y-5" onSubmit={(e) => e.preventDefault()}>
              <div>
                <label htmlFor="name" className="block text-sm font-bold text-gray-700 mb-1">Name</label>
                <input type="text" id="name" className="w-full rounded-lg border-gray-300 shadow-sm focus:border-green-600 focus:ring-green-600 p-3 bg-gray-50 border" placeholder="Dein Name" />
              </div>
              <div>
                <label htmlFor="klasse" className="block text-sm font-bold text-gray-700 mb-1">Klasse / Jahrgangsstufe</label>
                <input type="text" id="klasse" className="w-full rounded-lg border-gray-300 shadow-sm focus:border-green-600 focus:ring-green-600 p-3 bg-gray-50 border" placeholder="z.B. 6a oder EF" />
              </div>
              <div>
                <label htmlFor="message" className="block text-sm font-bold text-gray-700 mb-1">Nachricht</label>
                <textarea id="message" rows={4} className="w-full rounded-lg border-gray-300 shadow-sm focus:border-green-600 focus:ring-green-600 p-3 bg-gray-50 border" placeholder="Ich interessiere mich für das Anfängerwochenende..."></textarea>
              </div>
              <button type="submit" className="w-full bg-green-800 text-white px-4 py-3.5 rounded-lg font-bold text-lg hover:bg-green-700 transition-colors shadow-md">
                Nachricht absenden
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen flex flex-col bg-white font-sans text-gray-800 selection:bg-green-200">
      
      {/* CSS für weiche Übergänge (wird automatisch angewendet) */}
      <style>{`
        .animate-fadeIn { animation: fadeIn 0.4s ease-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
      `}</style>

      {/* Navigation */}
      <nav className="sticky top-0 w-full z-50 bg-green-800 text-white shadow-md">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-20">
            <div className="flex items-center cursor-pointer group" onClick={() => navigateTo('home')}>
              <SrvLogo className="h-16 w-24 mr-3 drop-shadow-sm group-hover:scale-105 transition-transform" />
            </div>
            
            {/* Desktop Menu */}
            <div className="hidden lg:flex space-x-2 items-center">
              {navLinks.map((link) => (
                <button 
                  key={link.id}
                  onClick={() => navigateTo(link.id)} 
                  className={`px-3 py-2 rounded-md transition-colors font-medium ${currentPage === link.id ? 'bg-green-900 text-white shadow-inner' : 'hover:bg-green-700 hover:text-white'}`}
                >
                  {link.label}
                </button>
              ))}
              
              {/* Trennstrich */}
              <div className="h-6 w-px bg-green-600 mx-2"></div>
              
              {/* Link zur Schulhomepage */}
              <a 
                href="https://kalkuhl.de/" 
                target="_blank" 
                rel="noopener noreferrer"
                className="flex items-center bg-white text-green-800 px-4 py-2 rounded-full hover:bg-green-50 transition-colors font-bold text-sm shadow-sm ml-2"
              >
                Kalkuhl.de <ExternalLink className="ml-1 h-4 w-4" />
              </a>
            </div>

            {/* Mobile Menu Button */}
            <div className="lg:hidden flex items-center">
              <button onClick={toggleMenu} className="text-white hover:bg-green-700 rounded-md focus:outline-none p-2">
                {isMenuOpen ? <X className="h-8 w-8" /> : <Menu className="h-8 w-8" />}
              </button>
            </div>
          </div>
        </div>

        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="lg:hidden bg-green-800 shadow-xl border-t border-green-700 max-h-[80vh] overflow-y-auto">
            <div className="px-4 pt-2 pb-6 space-y-2">
              {navLinks.map((link) => (
                <button 
                  key={link.id}
                  onClick={() => navigateTo(link.id)} 
                  className={`block w-full text-left px-4 py-3 rounded-md text-base font-medium transition-colors ${currentPage === link.id ? 'bg-green-900 text-white border-l-4 border-white' : 'hover:bg-green-700 text-green-100'}`}
                >
                  {link.label}
                </button>
              ))}
              
              <div className="pt-4 mt-2 border-t border-green-700">
                <a 
                  href="https://kalkuhl.de/" 
                  target="_blank" 
                  rel="noopener noreferrer"
                  className="flex items-center justify-center w-full bg-white text-green-800 px-4 py-3 rounded-md font-bold text-base shadow-sm"
                >
                  Zur Kalkuhl Homepage <ExternalLink className="ml-2 h-5 w-5" />
                </a>
              </div>
            </div>
          </div>
        )}
      </nav>

      {/* Hauptinhalt (Wechselt basierend auf currentPage) */}
      <main className="flex-grow bg-gray-50/50">
        {currentPage === 'home' && renderHome()}
        {currentPage === 'aktuelles' && renderAktuelles()}
        {currentPage === 'about' && renderAbout()}
        {currentPage === 'vorstand' && renderVorstand()}
        {currentPage === 'fleet' && renderFleet()}
        {currentPage === 'events' && renderEvents()}
        {currentPage === 'contact' && renderContact()}
      </main>

      {/* Footer */}
      <footer className="bg-green-950 text-green-300 py-12 mt-auto">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex flex-col md:flex-row justify-between items-center border-b border-green-800/50 pb-8 mb-8">
            <div className="flex items-center mb-6 md:mb-0 cursor-pointer" onClick={() => navigateTo('home')}>
              <div className="w-24 h-16 mr-4 opacity-80 bg-green-900 rounded-lg flex items-center justify-center border border-green-800">
                <SrvLogo className="w-full h-full p-1" />
              </div>
              <div>
                <span className="font-bold text-white text-xl block leading-tight">SRV am EKG</span>
                <span className="text-sm text-green-500">Gegründet 1976</span>
              </div>
            </div>
            <div className="flex space-x-6 font-medium text-sm md:text-base">
              <button onClick={() => navigateTo('about')} className="hover:text-white transition-colors">Bootshaus</button>
              <button onClick={() => navigateTo('events')} className="hover:text-white transition-colors">Termine</button>
              <button onClick={() => navigateTo('contact')} className="hover:text-white transition-colors">Kontakt</button>
            </div>
          </div>
          <div className="flex flex-col md:flex-row justify-between items-center text-sm">
            <span className="text-green-500 text-center md:text-left">&copy; {new Date().getFullYear()} Schüler-Ruder-Verein am Ernst-Kalkuhl-Gymnasium Bonn.</span>
            <div className="mt-6 md:mt-0 space-x-6 flex items-center">
              <a href="https://kalkuhl.de/" target="_blank" rel="noopener noreferrer" className="hover:text-white transition-colors flex items-center">
                EKG Homepage <ExternalLink className="ml-1 h-3 w-3" />
              </a>
              <a href="https://kalkuhl.de/impressum/" target="_blank" rel="noopener noreferrer" className="hover:text-white transition-colors">Impressum</a>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
}


