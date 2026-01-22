import React, { useState, useEffect } from 'react';
import { 
  Car, User, Lock, LogOut, Camera, MapPin, 
  Calendar, FileText, TrendingUp, Award, 
  BookOpen, Clock, CheckCircle, AlertCircle, 
  ShieldCheck, Settings, Users, ClipboardCheck,
  Wrench, Wallet, History, Navigation, Plus, 
  Fuel, Timer, ChevronRight, X, Download, Eye,
  Info, BellRing, Map, Package, Monitor, BarChart3,
  Smartphone, Hash, FileUp, Filter, Search
} from 'lucide-react';

const App = () => {
  // --- State Management ---
  const [user, setUser] = useState(null); 
  const [currentView, setCurrentView] = useState('peminjaman'); 
  const [isLoginView, setIsLoginView] = useState(false);
  const [ppnpnTab, setPpnpnTab] = useState('presensi');
  const [rtTab, setRtTab] = useState('kendaraan');
  const [currentTime, setCurrentTime] = useState(new Date());

  // Efek Jam Digital
  useEffect(() => {
    const timer = setInterval(() => setCurrentTime(new Date()), 1000);
    return () => clearInterval(timer);
  }, []);

  // --- Handlers ---
  const handleLogin = (roleType) => {
    const roles = {
      admin: { name: 'Admin Umum/RT', role: 'ADMIN', seksi: 'Subbag Umum' },
      atasan: { name: 'Kepala KPKNL', role: 'PIMPINAN', seksi: 'Manajemen' },
      pns: { name: 'Rahmat Hidayat', role: 'PNS', seksi: 'PKKN' },
      ppnpn: { name: 'Budi Santoso', role: 'PPNPN', seksi: 'Rumah Tangga' }
    };
    setUser(roles[roleType]);
    setIsLoginView(false);
    
    // Auto-view based on role
    if (roleType === 'admin') setCurrentView('admin_dashboard');
    else if (roleType === 'ppnpn') setCurrentView('ppnpn');
    else if (roleType === 'pns') setCurrentView('pns');
    else setCurrentView('atasan_dashboard');
  };

  const handleLogout = () => {
    setUser(null);
    setCurrentView('peminjaman');
  };

  // --- Components / UI Helpers ---
  const SectionHeader = ({ title, subtitle, icon: Icon, color = "blue" }) => (
    <div className="flex items-center gap-5 mb-8">
      <div className={`p-4 bg-gradient-to-br from-${color}-600 to-${color}-800 text-white rounded-3xl shadow-xl shadow-${color}-100`}>
        <Icon size={28}/>
      </div>
      <div>
        <h2 className="text-2xl font-black text-[#002855]">{title}</h2>
        <p className="text-xs font-bold text-slate-400 uppercase tracking-[0.2em]">{subtitle}</p>
      </div>
    </div>
  );

  // --- 1. MODUL RUMAH TANGGA (PUBLIK/CAMPURAN) ---
  const RumahTanggaView = () => (
    <div className="space-y-8 animate-in fade-in slide-in-from-bottom-4 duration-500">
      <div className="flex flex-col md:flex-row justify-between items-start md:items-end gap-6 bg-white p-8 rounded-[3rem] border border-slate-200 shadow-sm">
        <SectionHeader title="Modul Rumah Tangga" subtitle="Layanan Sarana & Prasarana" icon={Package} />
        
        <div className="flex bg-slate-100 p-1.5 rounded-[2rem] gap-1 w-full md:w-auto overflow-x-auto">
          {[
            { id: 'kendaraan', label: 'Kendaraan', icon: <Car size={14}/> },
            { id: 'pengadaan', label: 'Pengadaan', icon: <Plus size={14}/> },
            { id: 'inventaris', label: 'Elektronik', icon: <Monitor size={14}/> }
          ].map(tab => (
            <button 
              key={tab.id}
              onClick={() => setRtTab(tab.id)}
              className={`flex items-center gap-2 px-6 py-3.5 rounded-[1.5rem] text-[10px] font-black uppercase tracking-widest transition-all whitespace-nowrap ${rtTab === tab.id ? 'bg-[#002855] text-white shadow-lg' : 'text-slate-400 hover:bg-white'}`}
            >
              {tab.icon} {tab.label}
            </button>
          ))}
        </div>
      </div>

      {rtTab === 'kendaraan' && (
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          {[
            { unit: 'Avanza A 1234 BK', status: 'Dipinjam', user: 'Seksi HI', fuel: '4 Bar' },
            { unit: 'Rush A 1122 CP', status: 'Tersedia', user: '-', fuel: 'Full' },
            { unit: 'Vario A 5678 CP', status: 'Tersedia', user: '-', fuel: 'Full' },
            { unit: 'KLX A 9900 B', status: 'Booking', user: 'Seksi RSK', fuel: '2 Bar' },
          ].map((v, i) => (
            <div key={i} className="bg-white p-6 rounded-[2.5rem] border border-slate-200 hover:shadow-xl transition-all group">
              <div className="flex justify-between mb-6">
                <div className="p-3 bg-slate-50 text-slate-400 rounded-xl group-hover:bg-[#002855] group-hover:text-white transition-all"><Car size={20}/></div>
                <span className={`text-[8px] font-black px-3 py-1 rounded-full uppercase ${v.status === 'Tersedia' ? 'bg-green-100 text-green-600' : 'bg-amber-100 text-amber-600'}`}>{v.status}</span>
              </div>
              <h4 className="font-black text-slate-800">{v.unit}</h4>
              <div className="mt-4 space-y-2">
                <div className="flex justify-between text-[10px] font-bold uppercase text-slate-400">
                  <span>Peminjam:</span> <span className="text-slate-600">{v.user}</span>
                </div>
                <div className="flex justify-between text-[10px] font-bold uppercase text-slate-400">
                  <span>BBM:</span> <span className="text-slate-600">{v.fuel}</span>
                </div>
              </div>
              <button className="w-full mt-6 py-3 bg-[#002855] text-white text-[10px] font-black rounded-xl uppercase hover:bg-blue-800 transition-colors">
                {v.status === 'Tersedia' ? 'Pinjam Sekarang' : 'Booking Jadwal'}
              </button>
            </div>
          ))}
        </div>
      )}

      {rtTab === 'inventaris' && (
        <div className="bg-white rounded-[3rem] border border-slate-200 overflow-hidden">
          <table className="w-full text-left">
            <thead>
              <tr className="bg-slate-50 text-[10px] font-black uppercase text-slate-400 tracking-widest">
                <th className="px-8 py-6">Nama Barang</th>
                <th className="px-8 py-6">Merek / Tipe</th>
                <th className="px-8 py-6">No. Inventaris</th>
                <th className="px-8 py-6">Pengguna (Seksi)</th>
                <th className="px-8 py-6">Aksi</th>
              </tr>
            </thead>
            <tbody className="divide-y divide-slate-100">
              {[
                { nama: 'Laptop Workstation', merek: 'Dell Latitude 5420', no: '3.05.02.01.001', user: 'Rahmat (PKKN)' },
                { nama: 'PC All-in-One', merek: 'HP Pavilion 24', no: '3.05.02.01.042', user: 'Siti (Umum)' },
                { nama: 'Scanner High Speed', merek: 'Fujitsu iX1600', no: '3.05.02.05.012', user: 'Aris (HI)' },
              ].map((item, i) => (
                <tr key={i} className="text-sm font-medium hover:bg-slate-50 transition-colors">
                  <td className="px-8 py-5 font-black text-[#002855]">{item.nama}</td>
                  <td className="px-8 py-5 text-slate-500">{item.merek}</td>
                  <td className="px-8 py-5 font-mono text-xs text-slate-400">{item.no}</td>
                  <td className="px-8 py-5 text-slate-600 font-bold">{item.user}</td>
                  <td className="px-8 py-5">
                    <button className="p-2 bg-blue-50 text-blue-600 rounded-lg"><History size={16}/></button>
                  </td>
                </tr>
              ))}
            </tbody>
          </table>
        </div>
      )}
    </div>
  );

  // --- 2. MODUL PNS ---
  const PNSView = () => (
    <div className="space-y-8 animate-in fade-in slide-in-from-right-4 duration-500">
      <SectionHeader title="Portal Pegawai PNS" subtitle="Sistem Karier (Simka)" icon={User} color="blue" />
      
      <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
        {/* KGB */}
        <div className="bg-white p-8 rounded-[3rem] border border-slate-200 relative overflow-hidden group">
          <div className="flex items-center gap-4 mb-8">
            <div className="w-12 h-12 bg-blue-50 text-blue-600 rounded-2xl flex items-center justify-center"><TrendingUp size={24}/></div>
            <h3 className="font-black text-slate-800 text-lg">KGB Online</h3>
          </div>
          <div className="space-y-4">
            <div className="p-6 bg-slate-50 rounded-3xl border border-slate-100">
              <p className="text-[9px] text-slate-400 font-black uppercase tracking-widest">Estimasi KGB Berikutnya</p>
              <p className="text-2xl font-black text-[#002855] mt-1">01 Maret 2026</p>
            </div>
            <div className="flex items-center gap-3 text-green-600 bg-green-50 p-4 rounded-2xl border border-green-100 text-[10px] font-black uppercase tracking-tight">
               <ShieldCheck size={18}/> Status: Memenuhi Syarat
            </div>
          </div>
        </div>

        {/* Pangkat */}
        <div className="bg-white p-8 rounded-[3rem] border border-slate-200 relative overflow-hidden group">
          <div className="flex items-center gap-4 mb-8">
            <div className="w-12 h-12 bg-amber-50 text-amber-600 rounded-2xl flex items-center justify-center"><Award size={24}/></div>
            <h3 className="font-black text-slate-800 text-lg">Kepangkatan</h3>
          </div>
          <div className="p-6 bg-amber-50/50 rounded-3xl border border-amber-100">
            <p className="text-[9px] text-amber-700 font-black uppercase tracking-widest">Pangkat / Golongan</p>
            <p className="text-xl font-black text-slate-800 mt-1 uppercase">Penata Muda / III.a</p>
          </div>
        </div>

        {/* Diklat / PJJ */}
        <div className="bg-white p-8 rounded-[3rem] border border-slate-200 relative overflow-hidden group">
          <div className="flex items-center gap-4 mb-8">
            <div className="w-12 h-12 bg-purple-50 text-purple-600 rounded-2xl flex items-center justify-center"><BookOpen size={24}/></div>
            <h3 className="font-black text-slate-800 text-lg">Diklat & PJJ</h3>
          </div>
          <div className="space-y-3">
            <div className="p-4 bg-slate-50 rounded-2xl flex justify-between items-center group/item hover:bg-purple-50 transition-colors">
              <div>
                <p className="text-[11px] font-black text-slate-700 leading-tight">PJJ Keuangan Negara</p>
                <p className="text-[9px] text-slate-400 font-bold uppercase mt-0.5">2025 • 40 JP</p>
              </div>
              <button className="text-purple-600"><FileUp size={16}/></button>
            </div>
            <button className="w-full py-3 border-2 border-dashed border-slate-200 rounded-2xl text-[9px] font-black text-slate-400 uppercase tracking-widest hover:border-purple-300 hover:text-purple-500 transition-all">+ Tambah Riwayat</button>
          </div>
        </div>
      </div>
    </div>
  );

  // --- 3. MODUL PPNPN ---
  const PPNPNView = () => (
    <div className="space-y-8 animate-in fade-in slide-in-from-left-4 duration-500">
      <SectionHeader title="Portal PPNPN" subtitle="Absensi & Payroll Digital" icon={Navigation} color="emerald" />
      
      <div className="flex bg-white p-2 rounded-[2.5rem] border border-slate-200 w-fit mx-auto shadow-sm">
        {['presensi', 'cuti', 'gaji'].map(id => (
          <button 
            key={id}
            onClick={() => setPpnpnTab(id)}
            className={`px-10 py-4 rounded-[2rem] text-[10px] font-black uppercase tracking-widest transition-all ${ppnpnTab === id ? 'bg-[#002855] text-white shadow-xl shadow-blue-900/30' : 'text-slate-400 hover:bg-slate-50'}`}
          >
            {id}
          </button>
        ))}
      </div>

      {ppnpnTab === 'presensi' && (
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
          <div className="lg:col-span-1 space-y-6">
            <div className="bg-white p-8 rounded-[3rem] border border-slate-200 shadow-sm relative overflow-hidden">
              <h3 className="font-black text-slate-800 mb-6 flex items-center gap-2 uppercase text-xs tracking-widest">
                 <Camera size={18} className="text-blue-600"/> Presensi Selfie
              </h3>
              <div className="aspect-square bg-slate-100 rounded-[2.5rem] border-4 border-white shadow-inner flex flex-col items-center justify-center gap-4 group cursor-pointer hover:bg-blue-50 transition-all">
                <div className="w-20 h-20 bg-white rounded-full flex items-center justify-center text-slate-300 group-hover:text-blue-500 shadow-md transition-all">
                  <Camera size={32}/>
                </div>
                <div className="text-center">
                  <p className="text-[10px] font-black text-slate-400 uppercase tracking-widest">Klik untuk Foto</p>
                  <div className="flex items-center gap-1.5 justify-center mt-2 text-[9px] font-bold text-green-500">
                    <MapPin size={10}/> Radius: 45m (Valid)
                  </div>
                </div>
              </div>
              <button className="w-full mt-8 bg-[#002855] text-white py-5 rounded-[1.5rem] font-black text-xs shadow-xl shadow-blue-900/20 active:scale-95 transition-transform">KIRIM PRESENSI</button>
            </div>
          </div>

          <div className="lg:col-span-2 space-y-6">
             <div className="bg-white rounded-[3rem] border border-slate-200 shadow-sm overflow-hidden">
                <div className="p-8 border-b border-slate-100 flex justify-between items-center">
                   <h3 className="font-black text-slate-800 text-xs uppercase tracking-widest">Kehadiran Januari 2026</h3>
                   <div className="flex gap-4">
                      <div className="text-right">
                        <p className="text-[10px] font-black text-slate-400 uppercase">Terlambat</p>
                        <p className="text-lg font-black text-red-500">2x</p>
                      </div>
                      <div className="text-right">
                        <p className="text-[10px] font-black text-slate-400 uppercase">Hadir</p>
                        <p className="text-lg font-black text-green-500">18x</p>
                      </div>
                   </div>
                </div>
                <div className="p-4">
                   {[1, 2, 3].map(i => (
                     <div key={i} className="flex items-center justify-between p-4 hover:bg-slate-50 rounded-2xl transition-colors">
                        <div className="flex items-center gap-4">
                           <div className="w-10 h-10 bg-slate-100 rounded-xl flex flex-col items-center justify-center text-[#002855]">
                              <span className="text-[10px] font-black">{20+i}</span>
                              <span className="text-[7px] font-black uppercase">Jan</span>
                           </div>
                           <div>
                              <p className="text-xs font-black text-slate-700">07:25:12</p>
                              <p className="text-[9px] font-bold text-slate-400 uppercase tracking-tighter">Kantor (Gedung A)</p>
                           </div>
                        </div>
                        <span className="text-[8px] font-black px-2 py-1 bg-green-100 text-green-600 rounded-lg uppercase">Tepat Waktu</span>
                     </div>
                   ))}
                </div>
             </div>
          </div>
        </div>
      )}

      {ppnpnTab === 'gaji' && (
        <div className="max-w-xl mx-auto bg-white p-10 rounded-[4rem] border border-slate-200 shadow-sm relative overflow-hidden">
           <div className="absolute top-0 right-0 p-10 opacity-5"><Wallet size={120}/></div>
           <div className="flex justify-between items-start mb-10">
              <SectionHeader title="Daftar Gaji" subtitle="Januari 2026" icon={Wallet} color="emerald"/>
              <button className="p-3 bg-slate-50 text-slate-400 rounded-2xl hover:text-blue-600"><Download size={20}/></button>
           </div>
           <div className="space-y-6">
              <div className="flex justify-between items-center p-4 border-b border-dashed border-slate-200">
                 <span className="text-xs font-bold text-slate-400 uppercase tracking-widest">Gaji Pokok</span>
                 <span className="text-sm font-black text-slate-800 tracking-tighter">Rp 3.500.000</span>
              </div>
              <div className="flex justify-between items-center p-4 border-b border-dashed border-slate-200 text-green-600">
                 <span className="text-xs font-bold uppercase tracking-widest">Uang Makan</span>
                 <span className="text-sm font-black tracking-tighter">+ Rp 600.000</span>
              </div>
              <div className="flex justify-between items-center p-4 border-b border-dashed border-slate-200 text-red-500">
                 <span className="text-xs font-bold uppercase tracking-widest">BPJS / Pajak</span>
                 <span className="text-sm font-black tracking-tighter">- Rp 120.000</span>
              </div>
              <div className="mt-8 p-8 bg-slate-900 text-white rounded-[2.5rem] flex justify-between items-center shadow-2xl shadow-blue-900/40">
                 <span className="text-[10px] font-black uppercase tracking-[0.2em] text-blue-300">Take Home Pay</span>
                 <span className="text-2xl font-black tracking-tighter italic">Rp 3.980.000</span>
              </div>
           </div>
        </div>
      )}
    </div>
  );

  // --- 4. DASHBOARD PIMPINAN ---
  const AtasanDashboard = () => (
    <div className="space-y-8 animate-in fade-in zoom-in duration-500">
       <SectionHeader title="Dashboard Pimpinan" subtitle="Monitoring Operasional Kantor" icon={BarChart3} color="blue"/>
       <div className="grid grid-cols-1 md:grid-cols-4 gap-6">
          {[
            { label: 'Kehadiran Hari Ini', val: '98%', sub: '2 Pegawai Cuti', icon: <Users size={20}/>, color: 'blue' },
            { label: 'Keterlambatan PPNPN', val: '5%', sub: 'Bulan Januari', icon: <Timer size={20}/>, color: 'red' },
            { label: 'Kendaraan Dinas', val: '4/6', sub: 'Unit Digunakan', icon: <Car size={20}/>, color: 'amber' },
            { label: 'Pagu Anggaran RT', val: '72%', sub: 'Realisasi Berjalan', icon: <Wallet size={20}/>, color: 'emerald' },
          ].map((stat, i) => (
            <div key={i} className="bg-white p-6 rounded-[2.5rem] border border-slate-200 shadow-sm">
               <div className={`w-10 h-10 bg-${stat.color}-50 text-${stat.color}-600 rounded-xl flex items-center justify-center mb-4`}>{stat.icon}</div>
               <p className="text-[10px] font-black text-slate-400 uppercase tracking-widest">{stat.label}</p>
               <h4 className="text-2xl font-black text-[#002855] mt-1">{stat.val}</h4>
               <p className="text-[10px] font-bold text-slate-400 mt-1 italic">{stat.sub}</p>
            </div>
          ))}
       </div>
       <div className="bg-white p-10 rounded-[3rem] border border-slate-200">
          <h3 className="font-black text-slate-800 mb-6 flex items-center gap-2 text-xs uppercase tracking-widest">
            <ClipboardCheck size={18} className="text-blue-600"/> Persetujuan Tertunda
          </h3>
          <div className="space-y-4">
             {[
               { tgl: '22 Jan', nama: 'Aris Setiawan', jenis: 'Cuti Tahunan (3 Hari)', status: 'Pending' },
               { tgl: '22 Jan', nama: 'Hendra Jaya', jenis: 'Pinjam Mobil - Survey Lapangan', status: 'Pending' }
             ].map((req, i) => (
               <div key={i} className="flex items-center justify-between p-5 bg-slate-50 rounded-2xl border border-slate-100">
                  <div className="flex items-center gap-4">
                     <span className="text-[10px] font-black text-slate-400 w-12">{req.tgl}</span>
                     <div>
                        <p className="text-xs font-black text-slate-800">{req.nama}</p>
                        <p className="text-[10px] font-bold text-slate-400 uppercase">{req.jenis}</p>
                     </div>
                  </div>
                  <div className="flex gap-2">
                     <button className="px-5 py-2 bg-white text-green-600 rounded-xl text-[9px] font-black border border-green-100 hover:bg-green-600 hover:text-white transition-all">SETUJUI</button>
                     <button className="p-2 bg-white text-red-400 rounded-xl border border-red-50 hover:bg-red-500 hover:text-white transition-all"><X size={16}/></button>
                  </div>
               </div>
             ))}
          </div>
       </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-slate-50 flex flex-col font-sans antialiased text-slate-900 selection:bg-blue-100 selection:text-blue-900 overflow-x-hidden">
      {/* Navbar */}
      <nav className="bg-white/80 backdrop-blur-2xl sticky top-0 z-50 border-b border-slate-200 px-6 md:px-12 py-5 flex justify-between items-center">
        <div className="flex items-center gap-5 cursor-pointer group" onClick={() => setCurrentView('peminjaman')}>
          <div className="w-12 h-12 bg-gradient-to-br from-[#002855] to-blue-900 rounded-[1.25rem] flex items-center justify-center font-black text-yellow-500 shadow-xl shadow-blue-900/20 group-hover:-rotate-6 transition-transform">S</div>
          <div className="hidden sm:block">
            <h1 className="text-xl font-black text-[#002855] leading-none tracking-tighter uppercase">Satu KPKNL</h1>
            <div className="text-[9px] text-slate-400 font-black uppercase tracking-[0.3em] mt-1.5 flex items-center gap-1.5">
               <div className="w-1.5 h-1.5 bg-green-500 rounded-full animate-pulse"></div> Digital Serang
            </div>
          </div>
        </div>

        {/* Dynamic Context Menu */}
        {user && (
          <div className="flex bg-slate-100 p-1.5 rounded-[1.5rem] gap-1 mx-4">
             {[
               { id: 'peminjaman', icon: <Package size={14}/>, label: 'Layanan RT' },
               { id: user.role.toLowerCase(), icon: <User size={14}/>, label: 'Karier Pegawai' },
             ].map(nav => (
               <button 
                key={nav.id} 
                onClick={() => setCurrentView(nav.id)}
                className={`flex items-center gap-2 px-6 py-2.5 rounded-[1.2rem] text-[9px] font-black uppercase tracking-widest transition-all ${currentView === nav.id ? 'bg-[#002855] text-white shadow-md' : 'text-slate-400 hover:bg-white'}`}
               >
                 {nav.icon} <span className="hidden md:inline">{nav.label}</span>
               </button>
             ))}
             {user.role === 'PIMPINAN' && (
               <button onClick={() => setCurrentView('atasan_dashboard')} className={`flex items-center gap-2 px-6 py-2.5 rounded-[1.2rem] text-[9px] font-black uppercase tracking-widest transition-all ${currentView === 'atasan_dashboard' ? 'bg-[#002855] text-white shadow-md' : 'text-slate-400 hover:bg-white'}`}>
                  <BarChart3 size={14}/> <span className="hidden md:inline">Monitoring</span>
               </button>
             )}
          </div>
        )}

        <div className="flex items-center gap-6">
          {user ? (
            <div className="flex items-center gap-5">
               <div className="text-right hidden sm:block">
                  <p className="text-xs font-black text-[#002855] leading-none mb-1">{user.name}</p>
                  <p className="text-[9px] font-black text-blue-600 uppercase tracking-widest bg-blue-50 px-2 py-0.5 rounded-md inline-block">{user.role}</p>
               </div>
               <button onClick={handleLogout} className="w-12 h-12 flex items-center justify-center bg-red-50 text-red-500 rounded-2xl hover:bg-red-500 hover:text-white transition-all shadow-sm active:scale-95">
                <LogOut size={20} />
              </button>
            </div>
          ) : (
            <button 
              onClick={() => setIsLoginView(true)} 
              className="bg-[#002855] text-white px-8 py-4 rounded-2xl font-black text-[10px] hover:bg-blue-800 transition-all flex items-center gap-3 shadow-2xl shadow-blue-900/20 group active:scale-95"
            >
              <Lock size={14} /> LOGIN PEGAWAI
            </button>
          )}
        </div>
      </nav>

      {/* Main Container */}
      <main className="flex-1 max-w-7xl mx-auto w-full p-6 md:p-12 pb-24">
        {currentView === 'peminjaman' && <RumahTanggaView />}
        {currentView === 'pns' && <PNSView />}
        {currentView === 'ppnpn' && <PPNPNView />}
        {currentView === 'atasan_dashboard' && <AtasanDashboard />}
        {currentView === 'admin_dashboard' && (
          <div className="bg-white p-24 rounded-[4rem] text-center border-2 border-dashed border-slate-200 max-w-2xl mx-auto">
             <div className="w-24 h-24 bg-red-50 text-red-600 rounded-full flex items-center justify-center mx-auto mb-8 shadow-inner">
                <ShieldCheck size={40}/>
             </div>
             <h2 className="text-3xl font-black text-slate-800 uppercase tracking-tighter">Admin Panel</h2>
             <p className="text-slate-400 font-bold mt-3 uppercase tracking-[0.2em] text-xs">Manajemen Database & Konfigurasi Sistem</p>
             <div className="grid grid-cols-2 gap-4 mt-12">
               <button className="p-6 bg-slate-50 rounded-3xl text-[10px] font-black uppercase text-slate-600 hover:bg-blue-50 hover:text-blue-600 transition-all">Manajemen User</button>
               <button className="p-6 bg-slate-50 rounded-3xl text-[10px] font-black uppercase text-slate-600 hover:bg-blue-50 hover:text-blue-600 transition-all">Audit System Log</button>
             </div>
          </div>
        )}
      </main>

      {/* Login Modal */}
      {isLoginView && (
        <div className="fixed inset-0 z-[120] flex items-center justify-center p-6">
          <div className="absolute inset-0 bg-[#001a35]/90 backdrop-blur-xl" onClick={() => setIsLoginView(false)} />
          <div className="w-full max-w-2xl relative animate-in zoom-in duration-300">
            <div className="bg-white p-12 rounded-[4rem] shadow-2xl border border-slate-100 relative overflow-hidden">
               <div className="absolute top-0 left-0 w-full h-2 bg-yellow-500"></div>
               <div className="text-center mb-12">
                  <h3 className="text-4xl font-black text-[#002855] tracking-tighter uppercase leading-none">Autentikasi Pegawai</h3>
                  <p className="text-slate-400 text-[10px] font-black uppercase tracking-[0.4em] mt-3 italic">Pilih Profil Sesuai Kewenangan</p>
               </div>
               <div className="grid grid-cols-1 sm:grid-cols-2 gap-5">
                  {[
                    { id: 'admin', label: 'Admin (Umum/RT)', icon: <ShieldCheck size={20}/>, color: 'bg-red-50 text-red-600', sub: 'Kelola RT & SDM' },
                    { id: 'atasan', label: 'Pimpinan Kantor', icon: <ClipboardCheck size={20}/>, color: 'bg-purple-50 text-purple-600', sub: 'Monitoring & Approval' },
                    { id: 'pns', label: 'Pegawai PNS', icon: <User size={20}/>, color: 'bg-blue-50 text-blue-600', sub: 'Karier & Layanan RT' },
                    { id: 'ppnpn', label: 'Pegawai PPNPN', icon: <Navigation size={20}/>, color: 'bg-green-50 text-green-600', sub: 'Presensi & Payroll' },
                  ].map(role => (
                    <button 
                      key={role.id}
                      onClick={() => handleLogin(role.id)}
                      className={`flex flex-col gap-2 p-8 rounded-[2.5rem] border-2 border-transparent transition-all text-left group ${role.color} hover:border-current hover:shadow-xl`}
                    >
                      <div className="w-12 h-12 bg-white rounded-2xl flex items-center justify-center shadow-sm group-hover:scale-110 transition-transform">{role.icon}</div>
                      <div className="mt-2">
                        <span className="font-black text-xs uppercase tracking-widest block">{role.label}</span>
                        <span className="text-[9px] font-bold opacity-60 uppercase tracking-tighter">{role.sub}</span>
                      </div>
                    </button>
                  ))}
               </div>
               <button onClick={() => setIsLoginView(false)} className="w-full mt-10 text-slate-300 font-black text-[10px] uppercase tracking-[0.5em] hover:text-red-500 transition-all">Batalkan Login</button>
            </div>
          </div>
        </div>
      )}

      {/* Floating Action / Help */}
      <button className="fixed bottom-10 right-10 w-16 h-16 bg-[#002855] text-yellow-500 rounded-full flex items-center justify-center shadow-2xl shadow-blue-900/40 hover:scale-110 active:scale-90 transition-all z-40">
         <BellRing size={24}/>
      </button>

      <footer className="p-12 text-center border-t border-slate-200 mt-auto bg-white/50">
        <div className="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
           <div className="flex items-center gap-3">
              <div className="w-8 h-8 bg-[#002855] rounded-lg flex items-center justify-center font-black text-yellow-500 text-xs">S</div>
              <p className="text-[10px] font-black text-slate-400 uppercase tracking-[0.2em]">KPKNL Serang • Satu Aplikasi, Semua Layanan</p>
           </div>
           <div className="flex gap-8">
              <p className="text-[9px] font-black text-slate-400 uppercase tracking-widest flex items-center gap-2"><Smartphone size={12}/> V2.0 STABLE</p>
              <p className="text-[9px] font-black text-slate-400 uppercase tracking-widest italic">Kemenkeu Satu • DJKN Terpercaya</p>
           </div>
        </div>
      </footer>
    </div>
  );
};

export default App;
