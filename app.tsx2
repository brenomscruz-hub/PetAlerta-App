import { RouterProvider, createBrowserRouter, Outlet, useNavigate, useLocation } from 'react-router';
import { Battery, Wifi, Signal, ChevronLeft, MapPin, Camera, Search, MessageCircle, Phone, X, Mic, MicOff, Volume2, VolumeX, Store, ShoppingCart, CircleHelp, Check, Navigation, BellRing, Wallet, Syringe, ShieldCheck, Minus, Plus, Car, Calendar } from 'lucide-react';
import { useEffect, useRef, useState } from 'react';
import emblem from './assets/logo-emblem.jpg';
import wordmark from './assets/logo-wordmark.jpg';

type Msg = { from: string; text: string };
type Person = { name: string; img: string; role: string; time: string; msgs: Msg[] };

const face = (kind: 'men' | 'women', n: number) => `https://randomuser.me/api/portraits/${kind}/${n}.jpg`;

const PEOPLE: Record<string, Person> = {
  marina: {
    name: 'Marina C.', img: face('women', 65), role: 'Tutora', time: '',
    msgs: [
      { from: 'me', text: 'Olá Marina! Acho que encontrei o Thor. Ele está perto da padaria na Av. das Américas, perto do IBMR Barra.' },
      { from: 'marina', text: 'Sério?! Graças a Deus! Ele está bem? Estou a 5 minutos daí, posso ligar?' },
    ],
  },
  henrique: {
    name: 'Henrique A.', img: face('men', 22), role: 'Avistou o pet', time: 'há 2h',
    msgs: [
      { from: 'henrique', text: 'Boa tarde. Avistei um beagle por volta das 14h, na Av. das Américas, próximo ao número 2603. Aparentava estar saudável e usava coleira azul.' },
      { from: 'henrique', text: 'Permaneci no local por alguns minutos, porém ele seguiu em direção ao Recreio. Fico à disposição.' },
    ],
  },
  thais: {
    name: 'Thaís', img: face('women', 26), role: 'Avistou o pet', time: 'há 45min',
    msgs: [
      { from: 'thais', text: 'oii!! vi um pug fofinho agora há pouco 😭 tava todo perdidinho perto do IBMR' },
      { from: 'thais', text: 'sem coleira mas manso demais kkkk deixei água pra ele' },
      { from: 'thais', text: 'tô por aqui ainda, fico de olho 🙏' },
    ],
  },
  jorge: {
    name: 'Seu Jorge', img: face('men', 54), role: 'Avistou o pet', time: 'há 1h',
    msgs: [
      { from: 'jorge', text: 'Boa tarde, minha filha. Eu vi essa gatinha aí na frente do BarraShopping. Tava toda assustada, coitada, escondida atrás de um vaso.' },
      { from: 'jorge', text: 'Dei um pouco de ração que eu tinha. Comeu e foi pro lado do estacionamento. Deus abençoe, tomara que acha.' },
    ],
  },
  fernanda: {
    name: 'Fernanda L.', img: face('women', 33), role: 'Avistou o pet', time: 'há 3h',
    msgs: [
      { from: 'fernanda', text: 'GENTE VI UMA GOLDEN AGORA NA PRAÇA DO Ó!!!' },
      { from: 'fernanda', text: 'correndo atrás de pombo, super feliz, sem noção nenhuma kkkk' },
      { from: 'fernanda', text: 'VEM RÁPIDO!!' },
    ],
  },
  marcos: {
    name: 'Marcos V.', img: face('men', 86), role: 'Avistou o pet', time: 'há 5h',
    msgs: [
      { from: 'marcos', text: 'jabuti marrom. lagoa de marapendi. 17h. andando na grama.' },
      { from: 'marcos', text: 'peguei e botei numa caixa. to c/ ele aq ainda.' },
    ],
  },
  priscila: {
    name: 'Priscila R.', img: face('women', 12), role: 'Avistou o pet', time: 'há 1 dia',
    msgs: [
      { from: 'priscila', text: 'Olá, tudo bem? Moro aqui perto e reconheci a Luna pelo cartaz que vi no grupo do condomínio. Ela é uma coelha branca e estava no jardim da Av. das Américas, em frente ao 2603, às 16h20, mais ou menos.' },
      { from: 'priscila', text: 'Tentei me aproximar devagar, como orienta o app, mas ela se escondeu entre as plantas. Estava solta e com as patinhas um pouco sujas de terra.' },
    ],
  },
  gabriel: {
    name: 'Gabriel S.', img: face('men', 5), role: 'Avistou o pet', time: 'há 1 dia',
    msgs: [
      { from: 'gabriel', text: 'fala! vi uma calopsita amarela ontem de noite pousada num poste perto da ciclovia 🐦' },
      { from: 'gabriel', text: 'n tenho certeza se é a sua, manda foto aí q eu confirmo' },
    ],
  },
  ricardo: {
    name: 'Ricardo M.', img: face('men', 32), role: 'Comunidade', time: 'há 10 min',
    msgs: [
      { from: 'ricardo', text: 'Vi um bichinho caramelo perto da padaria na Av. das Américas. Parecia assustado!' },
      { from: 'ricardo', text: 'Se eu passar por lá de novo te aviso.' },
    ],
  },
  juliana: {
    name: 'Juliana F.', img: face('women', 44), role: 'Comunidade', time: 'há 18 min',
    msgs: [
      { from: 'juliana', text: 'Gente, acho que acabei de ver ele!! Passou correndo na frente do IBMR, sentido Recreio 😱' },
      { from: 'juliana', text: 'Corri atrás mas não alcancei, desculpa!!' },
    ],
  },
  antonio: {
    name: 'Seu Antônio', img: face('men', 75), role: 'Comunidade', time: 'há 25 min',
    msgs: [
      { from: 'antonio', text: 'Meu filho, deixei uma tigela d\'água na portaria do prédio. Ele bebeu e seguiu pra praça.' },
      { from: 'antonio', text: 'Qualquer coisa o porteiro Cláudio está de plantão até as dez.' },
    ],
  },
  camila: {
    name: 'Camila R.', img: face('women', 68), role: 'Comunidade', time: 'há 40 min',
    msgs: [
      { from: 'camila', text: 'to de carro na Olegário Maciel, rodando o bairro' },
      { from: 'camila', text: 'aviso se vir algo. manda a foto dele pfv' },
    ],
  },
  lucas: {
    name: 'Lucas T.', img: face('men', 12), role: 'Comunidade', time: 'há 1h',
    msgs: [
      { from: 'lucas', text: 'Prezados, a segurança do shopping identificou um animal sem coleira no estacionamento G2.' },
      { from: 'lucas', text: 'O animal está sob observação. Favor comparecer com documento do tutor.' },
    ],
  },
  fatima: {
    name: 'Dona Fátima', img: face('women', 90), role: 'Comunidade', time: 'há 1h',
    msgs: [
      { from: 'fatima', text: 'Meu bem, ele tava deitadinho na calçada da Lagoa de Marapendi, cansado, coitadinho.' },
      { from: 'fatima', text: 'Fica calma que a gente acha ele, tá? Vou rezar por vocês 🙏' },
    ],
  },
};

const COMMUNITY_IDS = ['ricardo', 'juliana', 'antonio', 'camila', 'lucas', 'fatima'];

const GROUP: Msg[] = [
  { from: 'juliana', text: 'Gente, acho que acabei de ver ele!! Passou correndo na frente do IBMR, sentido Recreio 😱' },
  { from: 'camila', text: 'to indo praí agora, carro cinza' },
  { from: 'antonio', text: 'Boa tarde a todos. Deixei água na portaria, caso ele passe por aqui.' },
  { from: 'ricardo', text: 'Eu vi o caramelo perto da padaria mais cedo, tava assustado. Foi pro lado da praça.' },
  { from: 'lucas', text: 'Atenção: há um animal sem coleira no estacionamento G2 do shopping. Segurança acompanhando.' },
  { from: 'fatima', text: 'Meu Deus, que Deus proteja esse anjinho 🙏 Alguém tem foto pra eu mostrar pros vizinhos?' },
  { from: 'camila', text: 'foto no perfil do alerta' },
  { from: 'juliana', text: 'vou checar o G2!!! já chego' },
];

const TUTOR_AREAS = [
  { name: 'Recreio dos Bandeirantes', km: 8 },
  { name: 'Jacarepaguá', km: 10 },
  { name: 'São Conrado', km: 12 },
  { name: 'Tijuca', km: 20 },
  { name: 'Copacabana', km: 22 },
  { name: 'Centro', km: 28 },
];

const SIGHTINGS = [
  { name: 'Pipoca', emoji: '🐶', species: 'cao', breed: 'Beagle', when: 'há 2h', where: 'na Av. das Américas', who: 'henrique', img: 'https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=160&h=160&fit=crop' },
  { name: 'Bolinha', emoji: '🐶', species: 'cao', breed: 'Pug', when: 'há 45min', where: 'perto do IBMR Barra', who: 'thais', img: 'https://images.unsplash.com/photo-1517849845537-4d257902454a?w=160&h=160&fit=crop' },
  { name: 'Nina', emoji: '🐱', species: 'gato', breed: 'Gata SRD', when: 'há 1h', where: 'no BarraShopping', who: 'jorge', img: 'https://images.unsplash.com/photo-1536589961747-e239b2abbec2?w=160&h=160&fit=crop' },
  { name: 'Mel', emoji: '🐶', species: 'cao', breed: 'Golden Retriever', when: 'há 3h', where: 'na Praça do Ó', who: 'fernanda', img: 'https://images.unsplash.com/photo-1693615775129-f2004d6e3e0b?w=160&h=160&fit=crop' },
  { name: 'Tito', emoji: '🐢', species: 'tartaruga', breed: 'Jabuti', when: 'há 5h', where: 'na Lagoa de Marapendi', who: 'marcos', img: 'https://images.unsplash.com/photo-1597776941486-054bf5529210?w=160&h=160&fit=crop' },
  { name: 'Luna', emoji: '🐰', species: 'coelho', breed: 'Coelha', when: 'há 1 dia', where: 'na Av. das Américas', who: 'priscila', img: 'https://images.unsplash.com/photo-1585110396000-c9ffd4e4b308?w=160&h=160&fit=crop' },
  { name: 'Zeca', emoji: '🦜', species: 'ave', breed: 'Calopsita', when: 'há 1 dia', where: 'na ciclovia', who: 'gabriel', img: 'https://images.unsplash.com/photo-1517101724602-c257fe568157?w=160&h=160&fit=crop' },
];

function Logo({ className = '' }: { className?: string }) {
  return (
    <div className={`h-9 w-9 rounded-xl bg-white border border-gray-200 flex items-center justify-center overflow-hidden shrink-0 ${className}`}>
      <img src={emblem} alt="PetAlerta" className="h-8 w-auto" />
    </div>
  );
}

// --- FRAME 1: HOME ---
function Home() {
  const navigate = useNavigate();
  const [showAll, setShowAll] = useState(false);
  const visible = showAll ? SIGHTINGS : SIGHTINGS.slice(0, 2);
  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      {/* Banner */}
      <div className="bg-gradient-to-r from-surface-trust to-surface-hope px-5 pb-5 pt-16 rounded-b-[32px] shrink-0 flex flex-col gap-4">
        <div className="flex items-center gap-2">
          <img src={emblem} alt="" className="h-[64px] w-auto mix-blend-multiply shrink-0" />
          <img src={wordmark} alt="PetAlerta" className="h-[32px] w-auto mix-blend-multiply min-w-0" />
          <button onClick={() => navigate('/first-aid')} aria-label="Suporte e primeiros socorros" className="ml-auto w-11 h-11 rounded-full bg-white text-text-hope flex items-center justify-center shrink-0 border-2 border-text-hope/30">
            <CircleHelp size={24} />
          </button>
        </div>
        <div className="grid grid-cols-3 gap-3">
          {([
            { to: '/petshops', label: 'Pet Shops', icon: <Store size={22} /> },
            { to: '/shop', label: 'Loja', icon: <ShoppingCart size={22} /> },
            { to: '/premium', label: 'Premium', icon: <ShieldCheck size={22} /> },
          ]).map((q) => (
            <button key={q.to} onClick={() => navigate(q.to)} className="h-[64px] rounded-[16px] bg-white text-brand-trust flex flex-col items-center justify-center gap-1 border-2 border-brand-trust/30 text-xs font-bold">
              {q.icon}{q.label}
            </button>
          ))}
        </div>
      </div>

      {/* Primary Actions */}
      <div className="p-4 flex flex-col gap-4 mt-2">
        <button 
          onClick={() => navigate('/lost')}
          className="h-[120px] bg-surface-alert rounded-[24px] p-5 flex flex-col justify-center items-start border border-[#FDE68A] active:scale-[0.98] transition-transform"
        >
          <div className="bg-action-alert text-white p-2.5 rounded-full mb-3">
            <Search size={24} />
          </div>
          <h2 className="text-xl font-bold text-text-alert">Perdi meu Pet</h2>
          <p className="text-text-alert/80 text-sm font-medium mt-1">Alerta e Mapa Direto</p>
        </button>

        <button 
          onClick={() => navigate('/scanner')}
          className="h-[120px] bg-surface-hope rounded-[24px] p-5 flex flex-col justify-center items-start border border-[#A7F3D0] active:scale-[0.98] transition-transform"
        >
          <div className="bg-action-hope text-white p-2.5 rounded-full mb-3">
            <Camera size={24} />
          </div>
          <h2 className="text-xl font-bold text-text-hope">Encontrei um Pet</h2>
          <p className="text-text-hope/80 text-sm font-medium mt-1">Scanner Facial por IA</p>
        </button>
      </div>

      {/* Recent Sightings */}
      <div className="p-4 pt-2 flex-1">
        <h3 className="text-lg font-bold text-gray-900 mb-4">Avistamentos Recentes</h3>
        
        {visible.map((d) => (
          <div key={d.name} className="bg-white rounded-[24px] p-4 shadow-sm border border-gray-100 mb-4">
            <div className="flex gap-4">
              <div className="w-[80px] h-[80px] rounded-[16px] bg-gray-200 overflow-hidden shrink-0">
                <img src={d.img} alt={d.name} className="w-full h-full object-cover" />
              </div>
              <div className="flex-1 flex flex-col justify-between">
                <div>
                  <div className="flex justify-between items-start">
                    <h4 className="font-bold text-gray-900 text-lg leading-tight">{d.name}</h4>
                    <span className="bg-surface-alert text-text-alert text-xs font-bold px-2 py-1 rounded-full">Procurando</span>
                  </div>
                  <p className="text-gray-500 text-sm">{d.emoji} {d.breed} • {d.when} {d.where}</p>
                  <p className="flex items-center gap-1.5 text-xs font-semibold text-gray-700 mt-1.5">
                    <img src={PEOPLE[d.who].img} alt={PEOPLE[d.who].name} className="w-5 h-5 rounded-full object-cover" />
                    Visto por {PEOPLE[d.who].name}
                  </p>
                </div>
                <button
                  onClick={() => navigate('/chat', { state: { personId: d.who, petName: d.name, where: d.where } })}
                  className="mt-2 bg-surface-trust text-text-trust font-semibold text-sm py-2 px-4 rounded-[12px] flex items-center justify-center gap-2"
                >
                  <MessageCircle size={16} /> Contatar
                </button>
              </div>
            </div>
          </div>
        ))}
        <button
          onClick={() => setShowAll((v) => !v)}
          className="w-full h-[52px] bg-white text-text-trust rounded-[16px] font-bold text-base border-2 border-brand-trust/40 flex items-center justify-center gap-2 mb-6"
        >
          {showAll ? 'Ver Menos' : `Ver Mais (${SIGHTINGS.length - 2})`}
        </button>
      </div>
    </div>
  );
}

// --- FRAME 2: LOST PET FLOW ---
function LostDog() {
  const navigate = useNavigate();
  const [sex, setSex] = useState<'macho' | 'femea' | null>(null);
  const [species, setSpecies] = useState('');

  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-10">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full active:bg-gray-200">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <h1 className="text-lg font-bold text-gray-900 flex-1 leading-tight">Criar Alerta de Desaparecimento</h1>
        <button onClick={() => navigate('/first-aid')} aria-label="Dicas de primeiros socorros" className="w-11 h-11 rounded-full bg-surface-hope text-text-hope flex items-center justify-center shrink-0">
          <CircleHelp size={24} />
        </button>
        <Logo className="ml-auto" />
      </div>

      <div className="p-4 pt-0 flex flex-col gap-6 pb-8">
        <div className="bg-white p-5 rounded-[24px] border-[2px] border-surface-alert shadow-sm flex flex-col gap-5">
          <div>
            <label className="block text-sm font-bold text-gray-700 mb-2">Espécie do Pet</label>
            <input
              type="text"
              value={species}
              onChange={(e) => setSpecies(e.target.value)}
              placeholder="Ex: Cão, Gato, Tartaruga, Coelho, Calopsita"
              className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-alert focus:ring-2 focus:ring-surface-alert outline-none transition-all placeholder:text-gray-400"
            />
          </div>

          <div>
            <label className="block text-sm font-bold text-gray-700 mb-2">Nome do Pet</label>
            <input 
              type="text" 
              placeholder="Ex: Pipoca"
              className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-alert focus:ring-2 focus:ring-surface-alert outline-none transition-all placeholder:text-gray-400"
            />
          </div>

          <div>
            <label className="block text-sm font-bold text-gray-700 mb-2">Sexo do Pet</label>
            <div className="grid grid-cols-2 gap-3">
              {([['macho', 'Macho', '♂'], ['femea', 'Fêmea', '♀']] as const).map(([v, label, sym]) => (
                <button
                  key={v}
                  type="button"
                  aria-pressed={sex === v}
                  onClick={() => setSex(v)}
                  className={`h-[56px] rounded-[16px] font-bold text-base flex items-center justify-center gap-2 border-2 ${sex === v ? 'bg-action-alert text-white border-action-alert' : 'bg-gray-50 text-gray-700 border-gray-200'}`}
                >
                  <span className="text-xl leading-none">{sym}</span> {label}
                </button>
              ))}
            </div>
          </div>

          <div>
            <label className="block text-sm font-bold text-gray-700 mb-2">Foto para IA Biométrica</label>
            <button className="w-full h-[120px] rounded-[16px] border-2 border-dashed border-action-alert/40 bg-surface-alert/30 flex flex-col items-center justify-center gap-2 active:bg-surface-alert/50 transition-colors">
              <Camera size={28} className="text-action-alert" />
              <span className="text-sm font-semibold text-text-alert">Toque para selecionar imagem</span>
            </button>
            <div className="mt-3 flex items-start gap-2 bg-surface-alert p-3 rounded-[12px]">
              <span className="text-action-alert shrink-0">💡</span>
              <p className="text-xs font-bold text-text-alert leading-relaxed">
                Dica: mostre o rosto ou o padrão único do pet (focinho, casco, penas) para a biometria por IA
              </p>
            </div>
          </div>

          <div>
            <label className="block text-sm font-bold text-gray-700 mb-2">Último Local Visto</label>
            <div className="relative">
              <MapPin size={20} className="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400" />
              <input 
                type="text" 
                placeholder="Ex: Av. das Américas, próx. ao IBMR Barra"
                className="w-full h-[56px] bg-gray-50 rounded-[16px] pl-11 pr-4 text-base border border-gray-200 focus:border-action-alert focus:ring-2 focus:ring-surface-alert outline-none transition-all placeholder:text-gray-400"
              />
            </div>
          </div>

          <button 
            onClick={() => navigate('/tracking')}
            className="w-full h-[60px] bg-action-alert text-white rounded-[16px] font-bold text-lg mt-2 active:scale-[0.98] transition-transform shadow-lg shadow-action-alert/20"
          >
            Publicar Alerta Imediato
          </button>
        </div>
      </div>
    </div>
  );
}

// --- NOVO FRAME: RADAR DE BUSCAS (TRACKING) ---
function Tracking() {
  const navigate = useNavigate();

  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-30 border-b border-gray-100 shadow-sm">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full active:bg-gray-200">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <div>
          <h1 className="text-xl font-bold text-gray-900 leading-tight">Radar de Buscas</h1>
          <span className="text-xs font-bold text-action-alert flex items-center gap-1">
            <span className="relative flex h-2 w-2">
              <span className="animate-ping absolute inline-flex h-full w-full rounded-full bg-action-alert opacity-75"></span>
              <span className="relative inline-flex rounded-full h-2 w-2 bg-action-alert"></span>
            </span>
            Alerta Ativo
          </span>
        </div>
        <Logo className="ml-auto" />
      </div>

      <div className="p-4 flex flex-col gap-6 pb-8">
        <div className="w-full h-[280px] bg-surface-trust rounded-[24px] overflow-hidden relative isolate border border-blue-200 flex flex-col shadow-sm">
          <div className="p-3 bg-white/90 backdrop-blur-sm border-b border-white flex justify-between items-center relative z-10">
            <div className="flex items-center gap-2 text-text-trust font-bold text-sm">
              <span className="relative flex h-3 w-3">
                <span className="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span>
                <span className="relative inline-flex rounded-full h-3 w-3 bg-blue-500"></span>
              </span>
              GPS Ativo
            </div>
            <span className="text-xs font-bold text-text-trust bg-surface-trust px-2 py-1 rounded-full">IBMR Barra • Raio de 2km</span>
          </div>
          <div className="flex-1 relative">
            <iframe
              title="Mapa ao redor do IBMR Barra, Av. das Américas, 2603"
              src="https://www.openstreetmap.org/export/embed.html?bbox=-43.34803%2C-23.00563%2C-43.33203%2C-22.99563&layer=mapnik"
              className="absolute inset-0 w-full h-full border-0 pointer-events-none"
            />
            {[
              { l: '50%', t: '50%', c: 'bg-action-alert' },
              { l: '28%', t: '32%', c: 'bg-brand-trust' },
              { l: '72%', t: '38%', c: 'bg-brand-trust' },
              { l: '60%', t: '74%', c: 'bg-action-hope' },
            ].map((p, i) => (
              <div key={i} style={{ left: p.l, top: p.t }} className={`absolute -translate-x-1/2 -translate-y-1/2 p-1.5 ${p.c} text-white rounded-full shadow-lg border-2 border-white`}>
                <MapPin size={i === 0 ? 20 : 14} fill="currentColor" />
              </div>
            ))}
            <div className="absolute bottom-2 left-2 right-2 bg-white/90 backdrop-blur-sm rounded-[12px] px-3 py-1.5 text-xs font-bold text-gray-800 truncate">
              Av. das Américas, 2603 - Barra da Tijuca
            </div>
          </div>
        </div>
        
        <div className="bg-white p-5 rounded-[24px] border border-gray-100 shadow-sm flex flex-col gap-4">
          <h3 className="font-bold text-gray-900 text-lg">Atualizações da Comunidade</h3>
          {COMMUNITY_IDS.map((id) => {
            const c = PEOPLE[id];
            return (
              <button
                key={id}
                onClick={() => navigate('/chat', { state: { personId: id } })}
                className="flex items-start gap-3 p-4 bg-gray-50 rounded-[16px] border border-gray-100 text-left w-full"
              >
                <img src={c.img} alt={c.name} className="w-12 h-12 rounded-full object-cover shrink-0" />
                <div className="min-w-0">
                  <div className="flex items-center gap-2">
                    <h4 className="text-sm font-bold text-gray-900">{c.name}</h4>
                    <span className="text-xs text-gray-400">{c.time}</span>
                  </div>
                  <p className="text-sm text-gray-600 mt-0.5">{c.msgs[0].text}</p>
                </div>
              </button>
            );
          })}
          <button 
            onClick={() => navigate('/chat', { state: { personId: 'group' } })}
            className="w-full h-[52px] bg-surface-trust text-text-trust rounded-[16px] font-bold text-sm flex items-center justify-center gap-2 active:bg-blue-100 transition-colors mt-1"
          >
            <MessageCircle size={18} /> Abrir Chat da Comunidade ({COMMUNITY_IDS.length})
          </button>
        </div>
      </div>
    </div>
  );
}

// --- FRAME 3: CAMERA SCANNER ---
function Scanner() {
  const navigate = useNavigate();
  return (
    <div className="flex-1 bg-immersive flex flex-col relative overflow-hidden">
      {/* Background simulated camera feed */}
      <div className="absolute inset-0 opacity-40">
        <img src="https://images.unsplash.com/photo-1537151608828-ea2b11777ee8?w=800&h=1200&fit=crop" alt="Camera Feed" className="w-full h-full object-cover blur-sm" />
      </div>
      
      <div className="relative z-10 pt-14 pb-8 px-4 flex flex-col h-full">
        <div className="flex justify-between items-center">
          <button onClick={() => navigate(-1)} className="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center backdrop-blur text-white active:bg-white/20">
            <X size={24} />
          </button>
          <div className="bg-white/10 backdrop-blur px-4 py-2 rounded-full border border-white/20">
            <span className="text-white text-sm font-bold">Scanner Biométrica PetAlerta</span>
          </div>
          <Logo />
        </div>

        <div className="flex-1 flex flex-col items-center justify-center">
          <div className="relative w-[280px] h-[280px] rounded-full border-4 border-dashed border-scan-accent flex items-center justify-center mb-6">
            <div className="w-8 h-8 border-t-2 border-l-2 border-scan-accent absolute top-8 left-8"></div>
            <div className="w-8 h-8 border-t-2 border-r-2 border-scan-accent absolute top-8 right-8"></div>
            <div className="w-8 h-8 border-b-2 border-l-2 border-scan-accent absolute bottom-8 left-8"></div>
            <div className="w-8 h-8 border-b-2 border-r-2 border-scan-accent absolute bottom-8 right-8"></div>
            <div className="absolute inset-0 bg-scan-accent/10 rounded-full animate-pulse"></div>
            <span className="text-4xl opacity-50">🐾</span>
          </div>
          <div className="bg-white/10 backdrop-blur border border-white/20 px-5 py-3 rounded-[16px] flex items-center gap-3">
            <span className="text-xl">🎯</span>
            <span className="text-white font-bold text-sm">Centralize o pet dentro do círculo</span>
          </div>
        </div>

        <div className="mt-auto flex flex-col items-center gap-6">
          <div className="bg-black/50 backdrop-blur-md border border-white/10 p-4 rounded-[20px] w-full">
            <h4 className="text-white/70 text-xs font-bold uppercase tracking-wider mb-2">💡 Dicas de Captura</h4>
            <ul className="text-white text-sm font-medium space-y-2">
              <li className="flex items-center gap-2"><span>✨</span> Mantenha boa iluminação</li>
              <li className="flex items-center gap-2"><span>👤</span> Evite sombras sobre o rosto do pet</li>
            </ul>
          </div>
          
          <button 
            onClick={() => navigate('/analysis')}
            className="w-[88px] h-[88px] rounded-full bg-white/20 border-4 border-white flex items-center justify-center active:scale-95 transition-transform shrink-0 relative"
          >
            <div className="w-[64px] h-[64px] rounded-full bg-action-hope flex items-center justify-center text-white">
              <Camera size={32} fill="currentColor" />
            </div>
          </button>
          <span className="text-white font-bold text-sm">Tirar Foto e Analisar</span>
        </div>
      </div>
    </div>
  );
}

// --- FRAME 4: ANALYSIS ---
function Analysis() {
  const navigate = useNavigate();

  useEffect(() => {
    const timer = setTimeout(() => {
      navigate('/results');
    }, 3000);
    return () => clearTimeout(timer);
  }, [navigate]);

  return (
    <div className="flex-1 bg-immersive flex flex-col items-center justify-center relative overflow-hidden">
      <div className="absolute top-14 right-4 z-20"><Logo /></div>
      {/* Scanning Line */}
      <div className="absolute inset-0 z-0">
        <div className="w-full h-1 bg-scan-accent shadow-[0_0_15px_#34D399] animate-[scan_2s_ease-in-out_infinite_alternate]"></div>
      </div>

      <div className="relative z-10 flex flex-col items-center gap-8 px-8 w-full">
        <div className="w-[160px] h-[160px] relative flex items-center justify-center">
          <div className="absolute inset-0 border-[4px] border-scan-accent/30 rounded-full animate-[spin_4s_linear_infinite]"></div>
          <div className="absolute inset-4 border-[4px] border-scan-accent/50 rounded-full border-t-transparent animate-[spin_2s_linear_infinite_reverse]"></div>
          <div className="w-[80px] h-[80px] bg-scan-accent/20 rounded-full flex items-center justify-center backdrop-blur animate-pulse">
            <ScanIcon className="w-10 h-10 text-scan-accent" />
          </div>
        </div>

        <div className="text-center space-y-3">
          <h2 className="text-white font-bold text-xl">Processando IA Biométrica...</h2>
          <p className="text-scan-accent text-sm font-medium">Mapeando padrões biométricos únicos do pet...</p>
        </div>

        <div className="w-full h-3 bg-white/10 rounded-full overflow-hidden mt-4">
          <div className="h-full bg-scan-accent w-full animate-[progress_3s_ease-in-out]"></div>
        </div>
      </div>

      <style>{`
        @keyframes scan {
          0% { transform: translateY(0); }
          100% { transform: translateY(844px); }
        }
        @keyframes progress {
          0% { width: 0%; }
          100% { width: 100%; }
        }
      `}</style>
    </div>
  );
}

function ScanIcon(props: any) {
  return (
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" {...props}>
      <path d="M3 7V5a2 2 0 0 1 2-2h2"></path><path d="M17 3h2a2 2 0 0 1 2 2v2"></path><path d="M21 17v2a2 2 0 0 1-2 2h-2"></path><path d="M7 21H5a2 2 0 0 1-2-2v-2"></path><rect x="7" y="7" width="10" height="10" rx="2" ry="2"></rect>
    </svg>
  );
}

// --- FRAME 5: RESULTS ---
function Results() {
  const navigate = useNavigate();
  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-10 border-b border-gray-100">
        <button onClick={() => navigate('/')} className="p-2 -ml-2 rounded-full active:bg-gray-200">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <h1 className="text-xl font-bold text-gray-900">Resultados do Scanner</h1>
        <Logo className="ml-auto" />
      </div>

      <div className="p-4 flex flex-col gap-6 flex-1">
        <div className="flex justify-center">
          <div className="bg-surface-hope border border-action-hope/30 text-text-hope font-bold px-4 py-2 rounded-full flex items-center gap-2 shadow-sm text-sm">
            <span className="relative flex h-2 w-2">
              <span className="animate-ping absolute inline-flex h-full w-full rounded-full bg-action-hope opacity-75"></span>
              <span className="relative inline-flex rounded-full h-2 w-2 bg-action-hope"></span>
            </span>
            98% Compatível
          </div>
        </div>

        <div className="bg-white rounded-[24px] shadow-sm border border-gray-100 overflow-hidden flex flex-col">
          <div className="h-[200px] w-full bg-gray-200 relative">
            <img src="https://images.unsplash.com/photo-1558788353-f76d92427f16?w=600&h=400&fit=crop" alt="Thor" className="w-full h-full object-cover" />
            <div className="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent flex items-end p-5">
              <h2 className="text-3xl font-bold text-white">Thor</h2>
            </div>
            <div className="absolute top-4 left-4 bg-black/50 backdrop-blur text-white text-xs font-bold px-3 py-1.5 rounded-full">
              Caso #412
            </div>
          </div>
          
          <div className="p-5 flex flex-col gap-4">
            <div className="grid grid-cols-2 gap-4">
              <div>
                <span className="block text-xs font-bold text-gray-400 uppercase tracking-wider mb-1">Tutor</span>
                <span className="font-bold text-gray-900">Marina C.</span>
              </div>
              <div>
                <span className="block text-xs font-bold text-gray-400 uppercase tracking-wider mb-1">Último Local</span>
                <span className="font-bold text-gray-900">Barra da Tijuca, RJ</span>
              </div>
            </div>
            
            <div className="bg-gray-50 p-3 rounded-[12px] border border-gray-100">
              <span className="block text-xs font-bold text-gray-400 uppercase tracking-wider mb-1">Biometria (Marcas)</span>
              <p className="text-sm font-medium text-gray-700">Padrão de ranhuras no lado esquerdo do focinho altamente compatível com registro original.</p>
            </div>

            <button 
              onClick={() => navigate('/chat')}
              className="w-full h-[56px] bg-action-hope text-white rounded-[16px] font-bold text-base mt-2 flex items-center justify-center gap-2 whitespace-nowrap"
            >
              <MessageCircle size={20} className="shrink-0" /> Contatar Tutor
            </button>
          </div>
        </div>

        <div className="mt-auto mb-4">
          <button onClick={() => navigate('/register-found')} className="w-full bg-surface-trust p-4 rounded-[16px] border-2 border-brand-trust text-center">
            <span className="block font-bold text-brand-trust mb-1">Não é o pet certo?</span>
            <span className="text-sm font-medium text-text-trust/80">Cadastrar como Pet Achado sem Dono</span>
          </button>
        </div>
      </div>
    </div>
  );
}

// --- FRAME 6: CHAT / CALL ---
function Chat() {
  const navigate = useNavigate();
  const location = useLocation();
  const id: string = location.state?.personId ?? 'marina';
  const isGroup = id === 'group';
  const other = PEOPLE[isGroup ? 'marina' : id] ?? PEOPLE.marina;
  const petName: string | undefined = location.state?.petName;
  const canRescue = !isGroup && other.role === 'Avistou o pet' && !!petName;
  const [stage, setStage] = useState(0);
  const [area, setArea] = useState(0);
  const km = TUTOR_AREAS[area].km;
  const price = 3 * km;

  const [inCall, setInCall] = useState(false);
  const [muted, setMuted] = useState(false);
  const [speaker, setSpeaker] = useState(false);
  const [seconds, setSeconds] = useState(0);
  const [draft, setDraft] = useState('');
  const [messages, setMessages] = useState<Msg[]>(isGroup ? GROUP : other.msgs);
  const bottomRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!inCall) return;
    setSeconds(0);
    const t = setInterval(() => setSeconds((v) => v + 1), 1000);
    return () => clearInterval(t);
  }, [inCall]);

  useEffect(() => {
    bottomRef.current?.scrollIntoView({ block: 'end' });
  }, [messages, stage]);

  useEffect(() => {
    if (stage < 2 || stage > 4) return;
    const t = setTimeout(() => {
      setStage(stage + 1);
      if (stage === 3) setMessages((m) => [...m, { from: id, text: 'O carro chegou e o motorista já está com o pet. Ele está tranquilo!' }]);
      if (stage === 4) setMessages((m) => [...m, { from: 'me', text: `${petName} chegou em casa em segurança! Muito obrigado por tudo 💙` }]);
    }, stage === 2 ? 2500 : 5000);
    return () => clearTimeout(t);
  }, [stage, id, petName]);

  const confirmRescue = () => {
    setStage(2);
    setMessages((m) => [...m, { from: 'me', text: `Acionei o Carro PetAlerta para buscar ${petName} com você. Valor: ${brl(price)}. Chega em cerca de 8 min.` }]);
  };

  const steps = ['Procurando motorista', 'Motorista a caminho (8 min)', 'Pet a bordo, indo até você', 'Entregue com segurança'];

  const send = () => {
    const text = draft.trim();
    if (!text) return;
    setMessages((m) => [...m, { from: 'me', text }]);
    setDraft('');
  };

  const clock = `${String(Math.floor(seconds / 60)).padStart(2, '0')}:${String(seconds % 60).padStart(2, '0')}`;

  if (inCall) {
    return (
      <div className="flex-1 bg-immersive flex flex-col items-center pt-24 pb-12 px-6 relative">
        <div className="absolute top-14 right-4 z-20"><Logo /></div>
        <div className="relative z-10 flex flex-col items-center w-full flex-1">
          <div className="w-24 h-24 rounded-full bg-gray-200 mb-6 overflow-hidden border-2 border-white/20">
            <img src={other.img} alt={other.name} className="w-full h-full object-cover" />
          </div>
          <h2 className="text-2xl font-bold text-white mb-2 text-center">{other.name} - Chamada Privada</h2>
          <span className="text-white/60 font-medium font-mono text-xl">{clock}</span>
          <div className="mt-3 flex gap-2 text-xs font-bold">
            {muted && <span className="bg-white text-gray-900 px-3 py-1 rounded-full">Microfone mudo</span>}
            {speaker && <span className="bg-white text-gray-900 px-3 py-1 rounded-full">Viva-voz ligado</span>}
          </div>

          <div className="mt-auto w-full flex justify-center items-center gap-6 pb-12">
            <button
              onClick={() => setMuted((v) => !v)}
              aria-pressed={muted}
              className={`w-16 h-16 rounded-full flex items-center justify-center ${muted ? 'bg-white text-gray-900' : 'bg-white/10 text-white'}`}
            >
              {muted ? <MicOff size={24} /> : <Mic size={24} />}
            </button>
            <button
              onClick={() => setInCall(false)}
              className="w-20 h-20 rounded-full bg-red-500 text-white flex items-center justify-center shadow-lg shadow-red-500/20"
            >
              <Phone size={32} className="rotate-[135deg]" fill="currentColor" />
            </button>
            <button
              onClick={() => setSpeaker((v) => !v)}
              aria-pressed={speaker}
              className={`w-16 h-16 rounded-full flex items-center justify-center ${speaker ? 'bg-white text-gray-900' : 'bg-white/10 text-white'}`}
            >
              {speaker ? <Volume2 size={24} /> : <VolumeX size={24} />}
            </button>
          </div>
        </div>
      </div>
    );
  }

  return (
    <div className="flex-1 bg-white flex flex-col min-h-0">
      <div className="bg-white/90 backdrop-blur pt-14 pb-3 px-4 flex items-center justify-between border-b border-gray-100 z-10 shadow-sm shrink-0">
        <div className="flex items-center gap-3 min-w-0">
          <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full">
            <ChevronLeft size={28} className="text-gray-900" />
          </button>
          {isGroup ? (
            <>
              <div className="flex -space-x-3 shrink-0">
                {COMMUNITY_IDS.slice(0, 3).map((pid) => (
                  <img key={pid} src={PEOPLE[pid].img} alt={PEOPLE[pid].name} className="w-9 h-9 rounded-full object-cover border-2 border-white" />
                ))}
              </div>
              <div className="min-w-0">
                <h2 className="text-base font-bold text-gray-900 leading-tight">Chat da Comunidade</h2>
                <span className="text-xs font-medium text-green-600">{COMMUNITY_IDS.length} pessoas online</span>
              </div>
            </>
          ) : (
            <>
              <div className="w-10 h-10 rounded-full bg-gray-200 relative overflow-hidden shrink-0">
                <img src={other.img} alt={other.name} className="w-full h-full object-cover" />
                <div className="absolute bottom-0 right-0 w-3 h-3 bg-green-500 border-2 border-white rounded-full"></div>
              </div>
              <div className="min-w-0">
                <h2 className="text-base font-bold text-gray-900 leading-tight truncate">{other.name}</h2>
                <span className="text-xs font-medium text-green-600">{other.role} • Online</span>
              </div>
            </>
          )}
        </div>
        <div className="flex items-center gap-2 shrink-0">
          <Logo />
          {!isGroup && (
            <button onClick={() => setInCall(true)} className="w-10 h-10 rounded-full bg-action-hope text-white flex items-center justify-center shadow-md shadow-action-hope/20 shrink-0">
              <Phone size={20} fill="currentColor" />
            </button>
          )}
        </div>
      </div>

      <div className="bg-surface-alert px-4 py-3 border-b border-action-alert/20 flex gap-3 items-start shrink-0">
        <span className="text-xl">🔒</span>
        <p className="text-xs font-bold text-text-alert leading-relaxed mt-0.5">
          Sua privacidade está protegida. Telefones, CPF e sobrenomes estão ocultos.
        </p>
      </div>

      <div className="flex-1 min-h-0 p-4 flex flex-col gap-4 overflow-y-auto no-scrollbar">
        <div className="flex justify-center my-2">
          <span className="text-xs font-bold text-gray-400 uppercase tracking-wider bg-gray-50 px-3 py-1 rounded-full">Hoje</span>
        </div>
        {messages.map((m, i) => {
          if (m.from === 'me') {
            return (
              <div key={i} className="max-w-[85%] self-end">
                <div className="bg-surface-trust text-text-trust rounded-[20px] rounded-tr-sm p-4 text-sm font-medium border border-blue-200">{m.text}</div>
              </div>
            );
          }
          const who = PEOPLE[m.from] ?? other;
          return (
            <div key={i} className="flex gap-2 max-w-[85%] self-start">
              <img src={who.img} alt={who.name} className="w-8 h-8 rounded-full object-cover shrink-0 mt-auto" />
              <div>
                {isGroup && <span className="block text-xs font-bold text-gray-500 mb-1 ml-1">{who.name}</span>}
                <div className="bg-gray-100 text-gray-900 rounded-[20px] rounded-tl-sm p-4 text-sm font-medium">{m.text}</div>
              </div>
            </div>
          );
        })}
        {canRescue && (
          <div className="bg-gradient-to-br from-surface-trust to-surface-hope border-2 border-brand-trust/30 rounded-[20px] p-4 flex flex-col gap-3">
            <div className="flex items-center gap-3">
              <div className="w-11 h-11 rounded-full bg-brand-trust text-white flex items-center justify-center shrink-0"><Car size={22} /></div>
              <div>
                <h3 className="font-bold text-gray-900 leading-tight">Carro PetAlerta</h3>
                <p className="text-xs font-medium text-gray-600">Busca {petName} com {other.name} e leva até você</p>
              </div>
            </div>
            {stage === 0 && (
              <button onClick={() => setStage(1)} className="w-full h-[52px] bg-brand-trust text-white rounded-[14px] font-bold text-base flex items-center justify-center gap-2">
                <Car size={18} /> Acionar Carro PetAlerta
              </button>
            )}
            {stage === 1 && (
              <>
                <div className="bg-white/80 rounded-[14px] p-3 text-sm font-medium text-gray-700 flex flex-col gap-1.5">
                  <div className="flex justify-between gap-3"><span className="text-gray-500">Retirada</span><span className="text-right">Com {other.name}, perto de Av. das Américas, 2603</span></div>
                  <div className="flex justify-between items-center gap-3"><span className="text-gray-500">Seu bairro</span>
                    <select value={area} onChange={(e) => setArea(Number(e.target.value))} className="bg-white border border-gray-200 rounded-lg px-2 py-1 text-sm font-bold">
                      {TUTOR_AREAS.map((a, i) => <option key={a.name} value={i}>{a.name}</option>)}
                    </select></div>
                  <div className="flex justify-between gap-3"><span className="text-gray-500">Distância</span><span>{km} km</span></div>
                  <div className="flex justify-between gap-3"><span className="text-gray-500">Segurança</span><span className="text-right">Caixa com cinto, ar-condicionado, motorista verificado</span></div>
                  <div className="flex justify-between gap-3 pt-1.5 border-t border-gray-200 font-bold text-gray-900"><span>Valor ({km} km × R$ 3)</span><span>{brl(price)}</span></div>
                </div>
                <div className="grid grid-cols-2 gap-2">
                  <button onClick={() => setStage(0)} className="h-[48px] bg-white text-gray-700 rounded-[14px] font-bold text-sm">Cancelar</button>
                  <button onClick={confirmRescue} className="h-[48px] bg-action-hope text-white rounded-[14px] font-bold text-sm">Confirmar</button>
                </div>
              </>
            )}
            {stage >= 2 && (
              <ol className="flex flex-col gap-2">
                {steps.map((label, i) => {
                  const cur = stage - 2;
                  const done = i < cur || stage === 5;
                  const now = i === cur && stage < 5;
                  return (
                    <li key={label} className={`flex items-center gap-3 text-sm font-bold ${done ? 'text-text-hope' : now ? 'text-gray-900' : 'text-gray-400'}`}>
                      <span className={`w-6 h-6 rounded-full flex items-center justify-center shrink-0 ${done ? 'bg-action-hope text-white' : now ? 'bg-brand-trust text-white animate-pulse' : 'bg-gray-200'}`}>
                        {done ? <Check size={14} /> : <span className="text-xs">{i + 1}</span>}
                      </span>
                      {label}
                    </li>
                  );
                })}
              </ol>
            )}
          </div>
        )}
        <div ref={bottomRef} />
      </div>

      <div className="p-4 pb-8 bg-white border-t border-gray-100 shrink-0">
        <div className="flex items-center gap-2 bg-gray-100 rounded-full p-2 pr-4">
          <button className="w-10 h-10 rounded-full bg-white text-gray-500 flex items-center justify-center shadow-sm shrink-0">
            <Camera size={20} />
          </button>
          <input
            type="text"
            value={draft}
            onChange={(e) => setDraft(e.target.value)}
            onKeyDown={(e) => e.key === 'Enter' && send()}
            placeholder={isGroup ? 'Mensagem para a comunidade...' : 'Mensagem segura...'}
            className="flex-1 min-w-0 bg-transparent border-none outline-none text-sm font-medium px-2"
          />
          <button onClick={send} className="font-bold text-sm text-brand-trust rounded-full px-3 py-1">Enviar</button>
        </div>
      </div>
    </div>
  );
}

const AID_TIPS = [
  { icon: '😮', title: 'Engasgo', items: [
    'Abra a boca com cuidado. Se o objeto estiver visível, retire com os dedos ou uma pinça; nunca tente pegar o que não vê, para não empurrá-lo mais fundo.',
    'Cães médios e grandes: fique atrás e faça compressões firmes logo abaixo das costelas. Cães pequenos e gatos: segure de barriga para cima e comprima com dois dedos.',
    'Gatos: dê tapinhas firmes nas costas, entre as omoplatas.',
    'Mesmo que ele expulse o objeto, leve ao veterinário para avaliar danos.',
  ] },
  { icon: '🤢', title: 'Envenenamento e enjoo', items: [
    'Guarde a embalagem do produto ingerido: ela ajuda o veterinário a definir o tratamento.',
    'Não provoque vômito sem orientação veterinária. Com produtos cáusticos, como alvejante, o vômito piora a lesão.',
    'Não dê leite, óleo nem remédios caseiros.',
    'Ligue para a clínica veterinária informando o produto, a quantidade e o peso do pet.',
  ] },
  { icon: '🚗', title: 'Atropelamento ou queda', items: [
    'Use luvas ou um pano grosso: pets com dor podem morder até o próprio tutor.',
    'Evite mexer bruscamente por causa da coluna. Use tábua ou papelão grosso como maca.',
    'Controle sangramentos com gaze ou pano limpo e pressão constante; se encharcar, coloque outro por cima sem tirar o primeiro.',
    'Cubra com um cobertor e leve ao veterinário. Ligue antes para avisar.',
  ] },
  { icon: '⚡', title: 'Convulsão', items: [
    'Afaste objetos que possam machucar e cronometre a duração.',
    'Proteja a cabeça para que não bata no chão e não coloque a mão na boca.',
    'Mais de 5 minutos ou crises seguidas: emergência imediata.',
    'Depois, ele fica desorientado. Fale baixo, sem forçá-lo a se mover, e leve ao veterinário.',
  ] },
  { icon: '🥵', title: 'Golpe de calor', items: [
    'Leve a um local fresco e ofereça água aos poucos.',
    'Molhe levemente o corpo com água fresca, não gelada.',
    'Respiração ofegante e gengivas avermelhadas são sinais de alerta: procure o veterinário mesmo que ele melhore.',
  ] },
  { icon: '🚫', title: 'O que evitar', items: [
    'Dar remédios sem orientação veterinária.',
    'Usar álcool ou desinfetantes em feridas abertas.',
    'Retirar objetos cravados (pregos, vidros) ou tentar recolocar ossos.',
    'Lembre: primeiros socorros só ganham tempo. Procure um veterinário o quanto antes.',
  ] },
];

// --- FRAME 7: FIRST AID ---
function FirstAid() {
  const navigate = useNavigate();
  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-10 border-b border-gray-100">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full active:bg-gray-200">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <div>
          <h1 className="text-xl font-bold text-gray-900 leading-tight">Suporte e Primeiros Socorros</h1>
          <a href="tel:1746" className="text-sm font-bold text-red-600 flex items-center gap-1 mt-0.5">
            <Phone size={14} fill="currentColor" /> Animal ferido? Ligue 1746
          </a>
        </div>
        <Logo className="ml-auto" />
      </div>

      <div className="p-4 flex flex-col gap-4">
        <details className="group bg-surface-hope rounded-[20px] border border-[#A7F3D0] overflow-hidden" open>
          <summary className="flex items-center justify-between p-5 font-bold text-text-hope cursor-pointer select-none outline-none">
            <div className="flex items-center gap-3 text-lg">
              <span>⏱️</span> Primeiros 30 minutos após a fuga
            </div>
            <div className="w-8 h-8 rounded-full bg-white/50 flex items-center justify-center group-open:rotate-180 transition-transform">
              <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" strokeWidth="2" fill="none"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </div>
          </summary>
          <div className="px-5 pb-5 pt-0 text-text-hope/90 text-sm font-medium space-y-3">
            <p>1. <strong>Não corra atrás dele.</strong> Isso ativa o instinto de presa e ele correrá mais rápido.</p>
            <p>2. Deixe o portão aberto ou itens com o seu cheiro (uma camiseta usada) no local por onde ele fugiu.</p>
            <p>3. Avise os vizinhos num raio de 1 quarteirão imediatamente.</p>
          </div>
        </details>

        <details className="group bg-surface-hope rounded-[20px] border border-[#A7F3D0] overflow-hidden">
          <summary className="flex items-center justify-between p-5 font-bold text-text-hope cursor-pointer select-none outline-none">
            <div className="flex items-center gap-3 text-lg">
              <span>🐕</span> Cães: como aproximar-se
            </div>
            <div className="w-8 h-8 rounded-full bg-white/50 flex items-center justify-center group-open:rotate-180 transition-transform">
              <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" strokeWidth="2" fill="none"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </div>
          </summary>
          <div className="px-5 pb-5 pt-0 text-text-hope/90 text-sm font-medium space-y-3">
            <p>• Aproxime-se de lado, não de frente.</p>
            <p>• Evite contato visual direto prolongado (pode ser visto como ameaça).</p>
            <p>• Abaixe-se para ficar menor e menos intimidador.</p>
            <p>• Ofereça petiscos jogando-os suavemente perto dele.</p>
          </div>
        </details>

        <details className="group bg-surface-hope rounded-[20px] border border-[#A7F3D0] overflow-hidden">
          <summary className="flex items-center justify-between p-5 font-bold text-text-hope cursor-pointer select-none outline-none">
            <div className="flex items-center gap-3 text-lg"><span>🐱</span> Gatos, coelhos e roedores</div>
            <div className="w-8 h-8 rounded-full bg-white/50 flex items-center justify-center group-open:rotate-180 transition-transform">
              <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" strokeWidth="2" fill="none"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </div>
          </summary>
          <div className="px-5 pb-5 pt-0 text-text-hope/90 text-sm font-medium space-y-3">
            <p>• Fale baixo e evite movimentos bruscos; esses pets se escondem quando assustados.</p>
            <p>• Deixe comida e água perto do esconderijo e afaste-se para ele sair sozinho.</p>
            <p>• Use uma caixa de transporte forrada com toalha para pegá-lo com segurança.</p>
          </div>
        </details>

        <details className="group bg-surface-hope rounded-[20px] border border-[#A7F3D0] overflow-hidden">
          <summary className="flex items-center justify-between p-5 font-bold text-text-hope cursor-pointer select-none outline-none">
            <div className="flex items-center gap-3 text-lg"><span>🦜</span> Aves e tartarugas</div>
            <div className="w-8 h-8 rounded-full bg-white/50 flex items-center justify-center group-open:rotate-180 transition-transform">
              <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" strokeWidth="2" fill="none"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </div>
          </summary>
          <div className="px-5 pb-5 pt-0 text-text-hope/90 text-sm font-medium space-y-3">
            <p>• Aves: não persiga. Coloque a gaiola do lado de fora com comida e chame pelo nome.</p>
            <p>• Tartarugas e jabutis: segure pelas laterais do casco, nunca pelo rabo, e mantenha longe do sol forte.</p>
            <p>• Guarde o pet em uma caixa ventilada até chegar ao tutor ou a um veterinário.</p>
          </div>
        </details>

        <h2 className="text-sm font-bold text-gray-500 uppercase tracking-wider mt-2">Emergências de saúde</h2>
        {AID_TIPS.map((t) => (
          <details key={t.title} className="group bg-surface-alert rounded-[20px] border border-[#FDE68A] overflow-hidden">
            <summary className="flex items-center justify-between p-5 font-bold text-text-alert cursor-pointer select-none outline-none">
              <div className="flex items-center gap-3 text-lg"><span>{t.icon}</span> {t.title}</div>
              <div className="w-8 h-8 rounded-full bg-white/50 flex items-center justify-center group-open:rotate-180 transition-transform">
                <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" strokeWidth="2" fill="none"><polyline points="6 9 12 15 18 9"></polyline></svg>
              </div>
            </summary>
            <div className="px-5 pb-5 pt-0 text-text-alert/90 text-sm font-medium space-y-3">
              {t.items.map((it) => <p key={it}>• {it}</p>)}
            </div>
          </details>
        ))}
      </div>
    </div>
  );
}

// --- FRAME 8: REGISTER FOUND DOG (NO MATCH) ---
function RegisterFound() {
  const navigate = useNavigate();
  const [submitted, setSubmitted] = useState(false);
  const [species, setSpecies] = useState('');

  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-10 border-b border-gray-100">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full active:bg-gray-200">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <h1 className="text-xl font-bold text-gray-900">Cadastrar Pet Encontrado</h1>
        <Logo className="ml-auto" />
      </div>

      <div className="p-4 flex flex-col gap-6 pb-8">
        {!submitted ? (
          <div className="bg-white p-5 rounded-[24px] border border-gray-200 shadow-sm flex flex-col gap-5">
            <div className="bg-surface-hope/30 p-3 rounded-[12px] border border-[#A7F3D0]">
              <p className="text-sm font-bold text-text-hope leading-relaxed">
                Nenhum dono compatível foi encontrado pela IA. Ajude a cadastrá-lo na rede de busca!
              </p>
            </div>

            <div>
              <label className="block text-sm font-bold text-gray-700 mb-2">Espécie do Pet</label>
              <input
                type="text"
                value={species}
                onChange={(e) => setSpecies(e.target.value)}
                placeholder="Ex: Cão, Gato, Tartaruga, Coelho, Calopsita"
                className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-hope focus:ring-2 focus:ring-surface-hope outline-none transition-all placeholder:text-gray-400"
              />
            </div>

            <div>
              <label className="block text-sm font-bold text-gray-700 mb-2">Raça ou Tipo Físico</label>
              <input 
                type="text" 
                placeholder="Ex: Poodle, Siamês, Jabuti, Vira-lata"
                className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-hope focus:ring-2 focus:ring-surface-hope outline-none transition-all placeholder:text-gray-400"
              />
            </div>

            <div>
              <label className="block text-sm font-bold text-gray-700 mb-2">Cor Predominante</label>
              <input 
                type="text" 
                placeholder="Ex: Caramelo, Preto, Branco com manchas"
                className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-hope focus:ring-2 focus:ring-surface-hope outline-none transition-all placeholder:text-gray-400"
              />
            </div>

            <div className="grid grid-cols-2 gap-4">
              <div>
                <label className="block text-sm font-bold text-gray-700 mb-2">Sexo</label>
                <select defaultValue="" className="w-full h-[56px] bg-gray-50 rounded-[16px] px-4 text-base border border-gray-200 focus:border-action-hope focus:ring-2 focus:ring-surface-hope outline-none transition-all text-gray-700">
                  <option value="" disabled>Selecione</option>
                  <option value="macho">Macho</option>
                  <option value="femea">Fêmea</option>
                  <option value="nao_sei">Não sei</option>
                </select>
              </div>
            </div>

            <div>
              <label className="block text-sm font-bold text-gray-700 mb-2">Local onde foi encontrado</label>
              <div className="relative">
                <MapPin size={20} className="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400" />
                <input 
                  type="text" 
                  placeholder="Rua, Bairro ou Ponto de referência"
                  className="w-full h-[56px] bg-gray-50 rounded-[16px] pl-11 pr-4 text-base border border-gray-200 focus:border-action-hope focus:ring-2 focus:ring-surface-hope outline-none transition-all placeholder:text-gray-400"
                />
              </div>
            </div>

            <button 
              onClick={() => setSubmitted(true)}
              className="w-full h-[60px] bg-action-hope text-white rounded-[16px] font-bold text-lg mt-2 active:scale-[0.98] transition-transform shadow-lg shadow-action-hope/20"
            >
              Publicar na Rede
            </button>
          </div>
        ) : (
          <div className="flex flex-col items-center justify-center pt-10 pb-8 animate-in fade-in slide-in-from-bottom-4 duration-300">
            <div className="w-24 h-24 bg-surface-hope text-action-hope rounded-full flex items-center justify-center mb-6 shadow-lg shadow-action-hope/20">
              <svg viewBox="0 0 24 24" width="48" height="48" stroke="currentColor" strokeWidth="2" fill="none" strokeLinecap="round" strokeLinejoin="round"><polyline points="20 6 9 17 4 12"></polyline></svg>
            </div>
            <h2 className="text-2xl font-bold text-gray-900 mb-2 text-center">Cadastro Concluído!</h2>
            <p className="text-gray-600 text-center mb-8 px-4">
              O pet foi adicionado ao mapa público. Se um tutor relatar perda, você será notificado.
            </p>
            <button 
              onClick={() => navigate('/')}
              className="w-full max-w-[280px] h-[56px] bg-white border-2 border-gray-200 text-gray-900 rounded-[16px] font-bold text-base active:bg-gray-50 transition-colors"
            >
              Voltar ao Início
            </button>
          </div>
        )}
      </div>
    </div>
  );
}

// --- PET SHOPS ---
type Shop = { id: string; name: string; dist: string; addr: string; open: string; rating: string; services: ('Tratamento' | 'Consultas' | 'Produtos')[] };
const SHOPS: Shop[] = [
  { id: 'a', name: 'Mundo Animal Barra', dist: '350 m', addr: 'Av. das Américas, 2501', open: 'Aberto até 20h', rating: '4,8', services: ['Tratamento', 'Consultas', 'Produtos'] },
  { id: 'd', name: 'Clínica Vet 24h Barra', dist: '700 m', addr: 'Av. das Américas, 2900', open: 'Aberto 24h', rating: '4,7', services: ['Tratamento', 'Consultas'] },
  { id: 'b', name: 'PetCenter Américas', dist: '900 m', addr: 'Av. das Américas, 3120', open: 'Aberto até 22h', rating: '4,6', services: ['Consultas', 'Produtos'] },
  { id: 'c', name: 'Au Au Spa & Shop', dist: '1,6 km', addr: 'Rua Olegário Maciel, 140', open: 'Aberto até 19h', rating: '4,9', services: ['Tratamento', 'Produtos'] },
];
const SLOTS = ['Hoje 15:30', 'Hoje 17:00', 'Amanhã 09:00', 'Amanhã 11:30'];
const REASONS = ['Consulta', 'Vacina', 'Tratamento', 'Banho e tosa'];

function ShopCard({ shop, first }: { shop: Shop; first: boolean }) {
  const navigate = useNavigate();
  const [open, setOpen] = useState(false);
  const [reason, setReason] = useState(REASONS[0]);
  const [slot, setSlot] = useState<string | null>(null);
  const [booked, setBooked] = useState<string | null>(null);
  const canBook = shop.services.includes('Consultas') || shop.services.includes('Tratamento');
  return (
    <div className={`bg-white rounded-[24px] p-4 border-2 shadow-sm flex flex-col gap-3 ${booked ? 'border-action-hope' : 'border-gray-100'}`}>
      <div className="flex gap-3">
        <div className="w-12 h-12 rounded-[14px] bg-surface-trust text-brand-trust flex items-center justify-center shrink-0"><Store size={24} /></div>
        <div className="flex-1 min-w-0">
          <div className="flex items-start justify-between gap-2">
            <h3 className="font-bold text-gray-900 leading-tight">{shop.name}</h3>
            <span className="text-xs font-bold text-text-hope bg-surface-hope px-2 py-1 rounded-full shrink-0">{shop.dist}</span>
          </div>
          <p className="text-sm text-gray-500 mt-0.5">{shop.addr}</p>
          <p className="text-xs font-semibold text-gray-600 mt-1">★ {shop.rating} • {shop.open}{first ? ' • Mais próximo' : ''}</p>
        </div>
      </div>
      <div className="flex flex-wrap gap-1.5">
        {shop.services.map((sv) => <span key={sv} className="text-xs font-bold text-text-trust bg-surface-trust px-2.5 py-1 rounded-full">{sv}</span>)}
      </div>

      {booked && (
        <div className="bg-surface-hope text-text-hope rounded-[14px] p-3 text-sm font-bold flex items-center gap-2"><Check size={18} /> {booked}</div>
      )}

      {open && !booked && (
        <div className="bg-gray-50 rounded-[16px] p-3 flex flex-col gap-3">
          <div className="flex flex-wrap gap-2">
            {REASONS.map((r) => (
              <button key={r} onClick={() => setReason(r)} aria-pressed={reason === r} className={`px-3 h-9 rounded-full text-xs font-bold border-2 ${reason === r ? 'bg-brand-trust text-white border-brand-trust' : 'bg-white text-gray-700 border-gray-200'}`}>{r}</button>
            ))}
          </div>
          <div className="grid grid-cols-2 gap-2">
            {SLOTS.map((sl) => (
              <button key={sl} onClick={() => setSlot(sl)} aria-pressed={slot === sl} className={`h-10 rounded-[12px] text-sm font-bold border-2 ${slot === sl ? 'bg-action-hope text-white border-action-hope' : 'bg-white text-gray-700 border-gray-200'}`}>{sl}</button>
            ))}
          </div>
          <button
            disabled={!slot}
            onClick={() => { setBooked(`${reason} marcada: ${slot}`); setOpen(false); }}
            className="h-[48px] bg-action-hope text-white rounded-[14px] font-bold text-sm disabled:opacity-40"
          >
            Confirmar agendamento
          </button>
        </div>
      )}

      <div className="grid grid-cols-3 gap-2">
        {canBook ? (
          <button onClick={() => setOpen((v) => !v)} className="h-[48px] bg-brand-trust text-white rounded-[14px] font-bold text-xs flex flex-col items-center justify-center leading-tight">
            <Calendar size={16} /> Marcar
          </button>
        ) : <div />}
        {shop.services.includes('Produtos') ? (
          <button onClick={() => navigate('/shop')} className="h-[48px] bg-surface-trust text-text-trust rounded-[14px] font-bold text-xs flex flex-col items-center justify-center leading-tight">
            <ShoppingCart size={16} /> Produtos
          </button>
        ) : <div />}
        <a
          href={`https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(shop.name + ' ' + shop.addr + ' Rio de Janeiro')}`}
          target="_blank" rel="noreferrer"
          className="h-[48px] bg-surface-hope text-text-hope rounded-[14px] font-bold text-xs flex flex-col items-center justify-center leading-tight border-2 border-text-hope/30"
        >
          <Navigation size={16} /> Levar meu pet
        </a>
      </div>
    </div>
  );
}

function PetShops() {
  const navigate = useNavigate();
  const [query, setQuery] = useState('');
  const [filter, setFilter] = useState<'Todos' | 'Tratamento' | 'Consultas' | 'Produtos'>('Todos');
  const list = SHOPS.filter((sh) =>
    (filter === 'Todos' || sh.services.includes(filter)) &&
    (sh.name + ' ' + sh.addr).toLowerCase().includes(query.trim().toLowerCase()),
  );
  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-30 border-b border-gray-100">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <div>
          <h1 className="text-xl font-bold text-gray-900 leading-tight">Pet Shops Próximos</h1>
          <span className="text-xs font-semibold text-gray-500">Perto de Av. das Américas, 2603</span>
        </div>
        <Logo className="ml-auto" />
      </div>
      <div className="p-4 flex flex-col gap-4 pb-8">
        <div className="relative">
          <Search size={20} className="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400" />
          <input
            value={query}
            onChange={(e) => setQuery(e.target.value)}
            placeholder="Buscar pet shop ou endereço"
            className="w-full h-[56px] bg-white rounded-[16px] pl-11 pr-4 text-base border border-gray-200 focus:border-brand-trust outline-none"
          />
        </div>
        <div className="flex gap-2 overflow-x-auto no-scrollbar -mx-4 px-4">
          {(['Todos', 'Tratamento', 'Consultas', 'Produtos'] as const).map((f) => (
            <button key={f} onClick={() => setFilter(f)} aria-pressed={filter === f} className={`px-4 h-10 rounded-full text-sm font-bold shrink-0 border-2 ${filter === f ? 'bg-brand-trust text-white border-brand-trust' : 'bg-white text-gray-700 border-gray-200'}`}>{f}</button>
          ))}
        </div>
        <p className="text-sm font-medium text-gray-600">Para tratar seu pet, marcar consultas ou comprar produtos.</p>
        {list.map((sh, i) => <ShopCard key={sh.id} shop={sh} first={i === 0 && filter === 'Todos' && !query} />)}
        {list.length === 0 && <p className="text-center text-gray-500 font-medium py-8">Nenhum pet shop encontrado.</p>}
      </div>
    </div>
  );
}

// --- SHOP (LOJA) ---
const brl = (v: number) => v.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
const SIZES = ['Coleira P', 'Coleira M', 'Coleira G', 'Clipe universal'];

function Shop() {
  const navigate = useNavigate();
  const [size, setSize] = useState(SIZES[1]);
  const [qty, setQty] = useState(1);
  const [done, setDone] = useState(false);

  if (done) {
    return (
      <div className="flex-1 bg-neutral-bg flex flex-col items-center justify-center px-6 text-center gap-4">
        <div className="w-24 h-24 bg-surface-hope text-action-hope rounded-full flex items-center justify-center"><Check size={48} /></div>
        <h2 className="text-2xl font-bold text-gray-900">Pedido confirmado!</h2>
        <p className="text-gray-600">{qty}x Rastreador PetAlerta GPS ({size}) a caminho. Ative no app assim que chegar.</p>
        <button onClick={() => navigate('/')} className="w-full max-w-[280px] h-[56px] bg-white border-2 border-gray-200 text-gray-900 rounded-[16px] font-bold">Voltar ao Início</button>
      </div>
    );
  }

  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-30 border-b border-gray-100">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <h1 className="text-xl font-bold text-gray-900">Loja PetAlerta</h1>
        <button onClick={() => navigate('/premium')} aria-label="Plano Premium" className="ml-auto w-11 h-11 rounded-full bg-surface-trust text-brand-trust flex items-center justify-center border-2 border-brand-trust/30">
          <ShieldCheck size={24} />
        </button>
        <Logo />
      </div>

      <div className="p-4 flex flex-col gap-4 pb-8">
        <div className="bg-white rounded-[24px] border border-gray-100 shadow-sm overflow-hidden">
          <div className="h-[170px] bg-gradient-to-br from-surface-trust to-surface-hope flex items-center justify-center relative">
            <div className="w-24 h-24 rounded-full bg-white/80 text-brand-trust flex items-center justify-center border-4 border-brand-trust/30"><Navigation size={44} /></div>
            <span className="absolute top-4 left-4 bg-action-alert text-white text-xs font-bold px-3 py-1.5 rounded-full">Para todos os pets</span>
          </div>
          <div className="p-5 flex flex-col gap-4">
            <div>
              <h2 className="text-xl font-bold text-gray-900">Rastreador PetAlerta GPS</h2>
              <p className="text-sm font-medium text-gray-600 mt-1">Coleira para cães e gatos e clipe para coelhos, aves e répteis.</p>
            </div>
            <ul className="flex flex-col gap-2 text-sm font-medium text-gray-800">
              <li className="flex gap-2"><Check size={18} className="text-action-hope shrink-0" /> Bateria com duração de mais de 18 meses</li>
              <li className="flex gap-2"><Check size={18} className="text-action-hope shrink-0" /> Mesma tecnologia de uma AirTag: celulares próximos ajudam a localizar</li>
              <li className="flex gap-2"><Check size={18} className="text-action-hope shrink-0" /> Resistente à água e leve para qualquer porte</li>
            </ul>
            <div>
              <span className="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Modelo</span>
              <div className="grid grid-cols-2 gap-2">
                {SIZES.map((sz) => (
                  <button key={sz} onClick={() => setSize(sz)} aria-pressed={size === sz} className={`h-11 rounded-[12px] text-sm font-bold border-2 ${size === sz ? 'bg-brand-trust text-white border-brand-trust' : 'bg-gray-50 text-gray-700 border-gray-200'}`}>{sz}</button>
                ))}
              </div>
            </div>
            <div className="flex items-center justify-between">
              <span className="text-2xl font-bold text-gray-900">{brl(189.9 * qty)}</span>
              <div className="flex items-center gap-3">
                <button onClick={() => setQty((q) => Math.max(1, q - 1))} aria-label="Diminuir" className="w-9 h-9 rounded-full bg-gray-100 flex items-center justify-center"><Minus size={16} /></button>
                <span className="font-bold w-4 text-center">{qty}</span>
                <button onClick={() => setQty((q) => q + 1)} aria-label="Aumentar" className="w-9 h-9 rounded-full bg-gray-100 flex items-center justify-center"><Plus size={16} /></button>
              </div>
            </div>
            <button onClick={() => setDone(true)} className="w-full h-[56px] bg-action-hope text-white rounded-[16px] font-bold text-lg">Comprar agora</button>
          </div>
        </div>
      </div>
    </div>
  );
}

// --- PREMIUM ---
function Premium() {
  const navigate = useNavigate();
  const [plan, setPlan] = useState<'mensal' | 'anual'>('mensal');
  const [done, setDone] = useState(false);

  if (done) {
    return (
      <div className="flex-1 bg-neutral-bg flex flex-col items-center justify-center px-6 text-center gap-4">
        <div className="w-24 h-24 bg-surface-trust text-brand-trust rounded-full flex items-center justify-center"><ShieldCheck size={48} /></div>
        <h2 className="text-2xl font-bold text-gray-900">Premium ativado!</h2>
        <p className="text-gray-600">Seu pet agora conta com a proteção reforçada do Focinho Protegido Premium.</p>
        <button onClick={() => navigate('/')} className="w-full max-w-[280px] h-[56px] bg-white border-2 border-gray-200 text-gray-900 rounded-[16px] font-bold">Voltar ao Início</button>
      </div>
    );
  }

  return (
    <div className="flex-1 bg-neutral-bg flex flex-col no-scrollbar overflow-y-auto">
      <div className="sticky top-0 bg-neutral-bg/90 backdrop-blur pt-14 pb-4 px-4 flex items-center gap-3 z-30 border-b border-gray-100">
        <button onClick={() => navigate(-1)} className="p-2 -ml-2 rounded-full">
          <ChevronLeft size={28} className="text-gray-900" />
        </button>
        <h1 className="text-xl font-bold text-gray-900">Plano Premium</h1>
      </div>

      <div className="p-4 flex flex-col gap-4 pb-8">
        <div className="bg-gradient-to-br from-surface-trust to-surface-hope rounded-[24px] p-5 border-2 border-brand-trust/30 flex flex-col gap-4">
          <div className="w-14 h-14 rounded-full bg-white text-brand-trust flex items-center justify-center"><ShieldCheck size={30} /></div>
          <h2 className="text-2xl font-bold text-gray-900 leading-tight">Focinho Protegido Premium</h2>
          <p className="text-sm font-medium text-gray-700 -mt-2">O app continua grátis. Assine para ter segurança reforçada se o seu pet se perder.</p>
          <ul className="flex flex-col gap-3 text-sm font-medium text-gray-800">
            <li className="flex gap-3"><BellRing size={20} className="text-brand-trust shrink-0" /><span><b>Super Alerta WhatsApp:</b> avisa todos os usuários num raio de até 10 km.</span></li>
            <li className="flex gap-3"><Wallet size={20} className="text-brand-trust shrink-0" /><span><b>Recompensa Garantida:</b> gestão de recompensa no app com caução segura.</span></li>
            <li className="flex gap-3"><Syringe size={20} className="text-brand-trust shrink-0" /><span><b>Carteira de Vacinação:</b> histórico digital na nuvem com alertas de vermífugo e vacinas.</span></li>
          </ul>
        </div>
        <div className="grid grid-cols-2 gap-3">
          {([['mensal', 'R$ 9,90', '/mês'], ['anual', 'R$ 89,00', '/ano']] as const).map(([v, price, per]) => (
            <button key={v} onClick={() => setPlan(v)} aria-pressed={plan === v} className={`rounded-[16px] p-4 text-left border-2 ${plan === v ? 'bg-white border-brand-trust' : 'bg-white/60 border-gray-200'}`}>
              <span className="block text-xs font-bold text-gray-500 uppercase">{v}</span>
              <span className="font-bold text-gray-900 text-xl">{price}</span><span className="text-xs text-gray-500">{per}</span>
            </button>
          ))}
        </div>
        <button onClick={() => setDone(true)} className="w-full h-[60px] bg-brand-trust text-white rounded-[16px] font-bold text-lg">Assinar Premium</button>
      </div>
    </div>
  );
}

// --- APP ROOT WITH MOCKUP WRAPPER ---

function useClock() {
  const fmt = () => new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' });
  const [time, setTime] = useState(fmt);
  useEffect(() => {
    const t = setInterval(() => setTime(fmt()), 15000);
    return () => clearInterval(t);
  }, []);
  return time;
}

function AppWrapper() {
  const location = useLocation();
  const time = useClock();
  const isImmersive = location.pathname === '/scanner' || location.pathname === '/analysis';

  return (
    <div className="fixed inset-0 bg-[#000000] flex items-center justify-center p-0 sm:p-4 md:p-6">
      {/* Mobile Mockup Wrapper */}
      <div className="w-full sm:max-w-[390px] h-full sm:max-h-[844px] bg-neutral-bg rounded-none sm:rounded-[48px] overflow-hidden relative border-0 sm:border-[3px] border-[#0F172A] shadow-[0_0_50px_rgba(0,0,0,0.5)] flex flex-col shrink-0">
        
        {/* Hardware Notch / Island */}
        <div className="absolute top-0 inset-x-0 h-8 hidden sm:flex justify-center z-50 pointer-events-none">
          <div className="w-[100px] sm:w-[120px] h-6 sm:h-7 bg-[#0F172A] rounded-b-[20px] sm:rounded-b-[24px]"></div>
        </div>

        {/* Status Bar */}
        <div className={`absolute top-0 inset-x-0 h-14 flex items-center justify-between px-6 z-40 pointer-events-none transition-colors ${isImmersive ? 'text-white' : 'text-gray-900'}`}>
          <span className="text-sm font-semibold pl-2 pt-1">{time}</span>
          <div className="flex items-center gap-2 pt-1">
            <Signal size={16} />
            <Wifi size={16} />
            <Battery size={18} />
          </div>
        </div>

        {/* Content Area */}
        <Outlet />

        {/* Home Indicator */}
        <div className="absolute bottom-2 inset-x-0 h-1 hidden sm:flex justify-center z-50 pointer-events-none">
          <div className={`w-[130px] h-1 rounded-full ${isImmersive ? 'bg-white/50' : 'bg-gray-900/50'}`}></div>
        </div>
      </div>
    </div>
  );
}

const router = createBrowserRouter([
  {
    path: '/',
    element: <AppWrapper />,
    children: [
      { index: true, element: <Home /> },
      { path: 'lost', element: <LostDog /> },
      { path: 'tracking', element: <Tracking /> },
      { path: 'scanner', element: <Scanner /> },
      { path: 'analysis', element: <Analysis /> },
      { path: 'results', element: <Results /> },
      { path: 'chat', element: <Chat /> },
      { path: 'first-aid', element: <FirstAid /> },
      { path: 'petshops', element: <PetShops /> },
      { path: 'shop', element: <Shop /> },
      { path: 'premium', element: <Premium /> },
      { path: 'register-found', element: <RegisterFound /> },
    ],
  },
]);

export default function App() {
  return <RouterProvider router={router} />;
}
