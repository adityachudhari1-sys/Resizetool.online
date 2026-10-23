<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ResizeTool — Live Animated Showcase & GitHub README Generator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;600;700&family=Inter:wght@400;500;600;700;800&family=Orbitron:wght@600;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Fira Code', 'monospace'],
                        cyber: ['Orbitron', 'sans-serif'],
                    },
                    animation: {
                        'float': 'float 4s ease-in-out infinite',
                        'pulse-glow': 'pulseGlow 3s ease-in-out infinite',
                        'gradient-x': 'gradientX 6s ease infinite',
                        'marquee': 'marquee 28s linear infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-6px)' },
                        },
                        pulseGlow: {
                            '0%, 100%': { opacity: '1', filter: 'drop-shadow(0 0 8px rgba(56, 189, 248, 0.5))' },
                            '50%': { opacity: '0.75', filter: 'drop-shadow(0 0 18px rgba(168, 85, 247, 0.8))' },
                        },
                        gradientX: {
                            '0%, 100%': { 'background-size': '200% 200%', 'background-position': 'left center' },
                            '50%': { 'background-size': '200% 200%', 'background-position': 'right center' },
                        },
                        marquee: {
                            '0%': { transform: 'translateX(0%)' },
                            '100%': { transform: 'translateX(-50%)' },
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom scrollbar */
        ::-webkit-scrollbar { width: 8px; height: 8px; }
        ::-webkit-scrollbar-track { background: #0f172a; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #475569; }
        
        .bg-grid-pattern {
            background-image: radial-gradient(rgba(255, 255, 255, 0.08) 1px, transparent 1px);
            background-size: 20px 20px;
        }
        @keyframes scanline {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(500%); }
        }
        .scanline-bar {
            animation: scanline 5s linear infinite;
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 font-sans min-h-screen flex flex-col selection:bg-indigo-500 selection:text-white">

    <!-- Top Navigation Bar (ResizeTool + GitHub Code Studio Switcher) -->
    <header class="border-b border-slate-800/80 bg-slate-900/80 backdrop-blur-md sticky top-0 z-40">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between gap-4">
            <div class="flex items-center space-x-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-sky-500 via-indigo-500 to-purple-600 flex items-center justify-center shadow-lg shadow-indigo-500/20 animate-pulse-glow">
                    <span class="font-extrabold text-white text-lg">↔</span>
                </div>
                <div>
                    <div class="flex items-center gap-2">
                        <span class="font-extrabold text-lg tracking-tight bg-gradient-to-r from-white via-sky-200 to-indigo-300 bg-clip-text text-transparent">
                            ResizeTool
                        </span>
                        <span class="inline-flex items-center gap-1 px-2.5 py-0.5 rounded-full text-[11px] font-semibold bg-emerald-500/15 text-emerald-300 border border-emerald-500/30">
                            <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
                            100% Private (No Uploads)
                        </span>
                    </div>
                    <p class="text-[11px] text-slate-400 hidden sm:block">⚡ Lightning Fast WebAssembly & Canvas Engine • Live Animated View + GitHub Code</p>
                </div>
            </div>

            <!-- Nav Links + Primary GitHub Copy Modal Trigger -->
            <div class="flex items-center gap-2 sm:gap-4">
                <nav class="hidden md:flex items-center gap-4 text-xs font-medium text-slate-300">
                    <a href="#tools-section" class="hover:text-sky-400 transition">Tools</a>
                    <a href="#all-tools-section" class="hover:text-sky-400 transition">All Tools</a>
                    <a href="#guides-section" class="hover:text-sky-400 transition">Guides</a>
                    <a href="#faq-section" class="hover:text-sky-400 transition">FAQ</a>
                    <a href="#about-section" class="hover:text-sky-400 transition">About</a>
                </nav>
                <a href="#github-code-studio" class="px-3.5 py-2 rounded-xl bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700 text-white text-xs font-semibold shadow-lg shadow-indigo-500/25 transition flex items-center gap-1.5">
                    <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                        <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.53 1.032 1.53 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd"/>
                    </svg>
                    <span>Get GitHub Paste Code</span>
                </a>
            </div>
        </div>
    </header>

    <!-- Main Container -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8 space-y-12">

        <!-- SECTION 1: DIRECT GITHUB CODE & ANIMATED SVG STUDIO (TOP PRIORITY FOR INSTANT COPY) -->
        <section id="github-code-studio" class="bg-slate-900/95 border border-indigo-500/30 rounded-3xl p-6 shadow-2xl shadow-indigo-500/10">
            <div class="flex flex-wrap items-center justify-between gap-4 pb-5 border-b border-slate-800">
                <div>
                    <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-xs font-semibold bg-indigo-500/15 text-indigo-300 border border-indigo-500/30 mb-2">
                        ⚡ Ready for Direct GitHub Paste (`README.md` & Animated SVG)
                    </span>
                    <h2 class="text-xl sm:text-2xl font-bold text-white">
                        ResizeTool — Live Animated SVG & GitHub README Code Generator
                    </h2>
                    <p class="text-xs sm:text-sm text-slate-400 mt-1">
                        Your entire pasted ResizeTool text is converted below into a live animated SVG banner, a complete formatted GitHub `README.md`, and an interactive animated webpage.
                    </p>
                </div>
                <div class="flex flex-wrap items-center gap-2.5">
                    <button id="copyFullReadmeBtn" class="px-4 py-2.5 rounded-xl bg-gradient-to-r from-emerald-500 to-teal-600 hover:from-emerald-600 hover:to-teal-700 text-white text-xs font-bold shadow-lg shadow-emerald-500/20 transition flex items-center gap-2">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3"/>
                        </svg>
                        <span id="copyFullReadmeText">Copy Complete Animated GitHub README.md</span>
                    </button>
                    <button id="downloadSvgBtn" class="px-4 py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold transition flex items-center gap-2 border border-slate-700">
                        <svg class="w-4 h-4 text-sky-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"/>
                        </svg>
                        Download `resizetool-animated.svg`
                    </button>
                </div>
            </div>

            <!-- Studio Grid: Left Customizer + Right Live SVG & Code Output -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 mt-6">
                
                <!-- Left Column: Pasted Text Preset Selector & Animation Controls (5 cols) -->
                <div class="lg:col-span-5 space-y-4">
                    <div class="bg-slate-950/90 border border-slate-800 rounded-2xl p-4">
                        <div class="flex items-center justify-between mb-2">
                            <label for="textInput" class="text-xs font-semibold text-slate-200 flex items-center gap-1.5">
                                <span class="w-2 h-2 rounded-full bg-sky-400"></span>
                                ResizeTool Text in Live SVG Animator
                            </label>
                            <span class="text-[11px] text-indigo-400 font-mono" id="lineCountBadge">6 Lines</span>
                        </div>

                        <!-- Quick Section Loader Buttons for the Pasted Text -->
                        <div class="flex flex-wrap gap-1.5 mb-2.5">
                            <button type="button" data-preset="hero" class="preset-btn px-2.5 py-1 rounded-lg text-[11px] font-medium bg-indigo-600 text-white transition">
                                Hero Summary
                            </button>
                            <button type="button" data-preset="tools" class="preset-btn px-2.5 py-1 rounded-lg text-[11px] font-medium bg-slate-800 hover:bg-slate-700 text-slate-300 transition">
                                15 Tool Modes
                            </button>
                            <button type="button" data-preset="features" class="preset-btn px-2.5 py-1 rounded-lg text-[11px] font-medium bg-slate-800 hover:bg-slate-700 text-slate-300 transition">
                                Why ResizeTool
                            </button>
                            <button type="button" data-preset="full" class="preset-btn px-2.5 py-1 rounded-lg text-[11px] font-medium bg-slate-800 hover:bg-slate-700 text-slate-300 transition">
                                Full Pasted Text
                            </button>
                        </div>

                        <textarea id="textInput" rows="5" 
                            class="w-full rounded-xl bg-slate-900 border border-slate-800 focus:border-indigo-500 text-slate-100 p-3 text-xs font-mono leading-relaxed transition outline-none resize-y">ResizeTool — 100% Private (No Uploads)
⚡ Lightning Fast WebAssembly & Canvas Engine
Free Online Image Compressor, Resizer & PDF Suite
Resize, crop & compress to 20KB, 50KB, 100KB in browser
🛡️ Zero-Server Privacy • 🎯 Precise KB Control • ⚡ Zero Wait Times
Engineered by Aditya G. Chudhari (resizetool@yahoo.com)</textarea>
                    </div>

                    <!-- Animation Style & Controls -->
                    <div class="bg-slate-950/90 border border-slate-800 rounded-2xl p-4 space-y-4">
                        <div class="grid grid-cols-2 gap-2" id="styleButtons">
                            <button type="button" data-style="typewriter" class="style-btn active px-3 py-2 rounded-xl border text-left transition flex items-center gap-2 bg-indigo-600/20 border-indigo-500 text-white">
                                <span>⌨️</span>
                                <div>
                                    <div class="text-xs font-semibold">Typewriter</div>
                                    <div class="text-[10px] text-slate-400">Live Typing SVG</div>
                                </div>
                            </button>
                            <button type="button" data-style="gradient" class="style-btn px-3 py-2 rounded-xl border border-slate-800 bg-slate-900/60 hover:bg-slate-800/60 text-left transition flex items-center gap-2 text-slate-300">
                                <span>🌈</span>
                                <div>
                                    <div class="text-xs font-semibold">Gradient Wave</div>
                                    <div class="text-[10px] text-slate-400">Flowing Colors</div>
                                </div>
                            </button>
                            <button type="button" data-style="neon" class="style-btn px-3 py-2 rounded-xl border border-slate-800 bg-slate-900/60 hover:bg-slate-800/60 text-left transition flex items-center gap-2 text-slate-300">
                                <span>⚡</span>
                                <div>
                                    <div class="text-xs font-semibold">Neon Glow</div>
                                    <div class="text-[10px] text-slate-400">Cyber Pulse</div>
                                </div>
                            </button>
                            <button type="button" data-style="glitch" class="style-btn px-3 py-2 rounded-xl border border-slate-800 bg-slate-900/60 hover:bg-slate-800/60 text-left transition flex items-center gap-2 text-slate-300">
                                <span>👾</span>
                                <div>
                                    <div class="text-xs font-semibold">Cyber Glitch</div>
                                    <div class="text-[10px] text-slate-400">RGB Split Shift</div>
                                </div>
                            </button>
                        </div>

                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-[11px] text-slate-400 mb-1">Multi-line Mode</label>
                                <select id="lineMode" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-2.5 py-1.5 text-xs text-slate-200 outline-none">
                                    <option value="stacked">Show All Lines Stacked</option>
                                    <option value="cycle">Cycle Lines One by One</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-[11px] text-slate-400 mb-1">Font Family</label>
                                <select id="fontFamily" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-2.5 py-1.5 text-xs text-slate-200 outline-none">
                                    <option value="'Fira Code', monospace">Fira Code (Mono)</option>
                                    <option value="'Inter', system-ui, sans-serif">Inter (Sans)</option>
                                    <option value="'Orbitron', sans-serif">Orbitron (Cyber)</option>
                                </select>
                            </div>
                        </div>

                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <div class="flex justify-between text-[11px] mb-1">
                                    <span class="text-slate-400">Font Size</span>
                                    <span id="fontSizeVal" class="text-sky-400 font-mono">20px</span>
                                </div>
                                <input id="fontSize" type="range" min="14" max="38" value="20" class="w-full accent-indigo-500 cursor-pointer">
                            </div>
                            <div>
                                <div class="flex justify-between text-[11px] mb-1">
                                    <span class="text-slate-400">Animation Speed</span>
                                    <span id="speedVal" class="text-sky-400 font-mono">4s</span>
                                </div>
                                <input id="animSpeed" type="range" min="1.5" max="10" step="0.5" value="4" class="w-full accent-indigo-500 cursor-pointer">
                            </div>
                        </div>

                        <div class="grid grid-cols-3 gap-2">
                            <div class="bg-slate-900 p-2 rounded-xl border border-slate-800 flex items-center gap-2">
                                <input type="color" id="primaryColor" value="#38bdf8" class="w-6 h-6 rounded cursor-pointer bg-transparent border-0">
                                <div>
                                    <div class="text-[10px] font-medium text-slate-300">Primary</div>
                                    <div id="primaryHex" class="text-[9px] text-slate-500 font-mono">#38BDF8</div>
                                </div>
                            </div>
                            <div class="bg-slate-900 p-2 rounded-xl border border-slate-800 flex items-center gap-2">
                                <input type="color" id="secondaryColor" value="#a855f7" class="w-6 h-6 rounded cursor-pointer bg-transparent border-0">
                                <div>
                                    <div class="text-[10px] font-medium text-slate-300">Accent</div>
                                    <div id="secondaryHex" class="text-[9px] text-slate-500 font-mono">#A855F7</div>
                                </div>
                            </div>
                            <div class="bg-slate-900 p-2 rounded-xl border border-slate-800 flex items-center gap-2">
                                <input type="color" id="bgColor" value="#0d1117" class="w-6 h-6 rounded cursor-pointer bg-transparent border-0">
                                <div>
                                    <div class="text-[10px] font-medium text-slate-300">Canvas</div>
                                    <label class="flex items-center gap-1 text-[9px] text-slate-400 cursor-pointer">
                                        <input type="checkbox" id="transparentBg" class="rounded accent-indigo-500"> Transp.
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Right Column: Live Animated SVG Preview & Direct GitHub Paste Code (7 cols) -->
                <div class="lg:col-span-7 flex flex-col space-y-4">
                    
                    <!-- Live Animated SVG Container -->
                    <div class="bg-slate-950/90 border border-slate-800 rounded-2xl p-4">
                        <div class="flex items-center justify-between mb-2.5">
                            <div class="flex items-center gap-2">
                                <span class="w-2.5 h-2.5 rounded-full bg-rose-500"></span>
                                <span class="w-2.5 h-2.5 rounded-full bg-amber-500"></span>
                                <span class="w-2.5 h-2.5 rounded-full bg-emerald-500"></span>
                                <span class="text-xs font-semibold text-slate-300 ml-1">LIVE ANIMATED SVG BANNER PREVIEW</span>
                            </div>
                            <button id="replayBtn" class="text-xs px-2.5 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 transition flex items-center gap-1">
                                ↻ Replay Animation
                            </button>
                        </div>
                        <div id="svgPreviewContainer" class="w-full min-h-[190px] max-h-[280px] rounded-xl border border-slate-800/90 bg-grid-pattern flex items-center justify-center p-3 overflow-auto">
                            <!-- Injected Live Animated SVG -->
                        </div>
                    </div>

                    <!-- GitHub Direct Paste Tabs -->
                    <div class="bg-slate-950/90 border border-slate-800 rounded-2xl p-4 flex-1 flex flex-col">
                        <div class="flex flex-wrap items-center justify-between gap-2 mb-3">
                            <div class="flex flex-wrap bg-slate-900 p-1 rounded-xl border border-slate-800 text-xs gap-1">
                                <button data-tab="full-readme" class="code-tab active px-3 py-1.5 rounded-lg bg-indigo-600 text-white font-semibold transition">
                                    1. Full Animated GitHub README.md (All Text)
                                </button>
                                <button data-tab="readme-api" class="code-tab px-3 py-1.5 rounded-lg text-slate-400 hover:text-white transition">
                                    2. Typing SVG Header Only
                                </button>
                                <button data-tab="svg-code" class="code-tab px-3 py-1.5 rounded-lg text-slate-400 hover:text-white transition">
                                    3. Raw Animated SVG Code
                                </button>
                            </div>

                            <button id="copyCodeBtn" class="px-4 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-semibold transition flex items-center gap-1.5 shadow-md">
                                <span id="copyBtnText">📋 Copy Selected Code</span>
                            </button>
                        </div>

                        <div id="tabInstruction" class="mb-2.5 px-3 py-2 rounded-xl bg-indigo-500/10 border border-indigo-500/20 text-xs text-indigo-200">
                            ⚡ <strong>Direct GitHub Paste:</strong> Copy & paste this directly into your GitHub repository's <code>README.md</code> file. It includes an animated typing SVG banner, badges, all 15 tools, guides, interactive FAQs, and credits!
                        </div>

                        <pre id="codeOutput" class="w-full flex-1 min-h-[180px] max-h-[240px] rounded-xl bg-slate-900 border border-slate-800 p-3.5 text-xs font-mono text-emerald-300 overflow-auto whitespace-pre-wrap break-words select-all"></pre>
                    </div>
                </div>
            </div>
        </section>

        <!-- ========================================================================= -->
        <!-- SECTION 2: LIVE ANIMATED WEB SHOWCASE OF ALL PASTED RESIZETOOL CONTENT   -->
        <!-- ========================================================================= -->
        <section class="space-y-12">
            
            <!-- Animated Hero Banner -->
            <div class="relative overflow-hidden rounded-3xl border border-slate-800 bg-gradient-to-b from-slate-900 via-slate-950 to-slate-900 p-6 sm:p-10 text-center shadow-2xl">
                <div class="absolute inset-0 bg-grid-pattern opacity-40 pointer-events-none"></div>
                
                <!-- Top Animated Badges -->
                <div class="relative z-10 flex flex-wrap items-center justify-center gap-2.5 mb-5">
                    <span class="inline-flex items-center gap-1.5 px-3.5 py-1.5 rounded-full text-xs font-semibold bg-emerald-500/10 text-emerald-400 border border-emerald-500/30 animate-float">
                        🛡️ 100% Private (No Uploads)
                    </span>
                    <span class="inline-flex items-center gap-1.5 px-3.5 py-1.5 rounded-full text-xs font-semibold bg-sky-500/10 text-sky-400 border border-sky-500/30">
                        ⚡ Lightning Fast WebAssembly & Canvas Engine
                    </span>
                </div>

                <!-- Animated Main Title -->
                <h1 class="relative z-10 text-3xl sm:text-5xl font-extrabold tracking-tight bg-gradient-to-r from-sky-400 via-indigo-300 to-purple-400 bg-clip-text text-transparent animate-gradient-x mb-4">
                    Free Online Image Compressor, Resizer & PDF Suite
                </h1>

                <!-- Live Typewriter Subtitle -->
                <p class="relative z-10 max-w-3xl mx-auto text-sm sm:text-base text-slate-300 leading-relaxed mb-8">
                    Resize, crop, and compress images to custom KB limits (<span class="text-sky-400 font-semibold">20KB, 50KB, 100KB</span>) for official exam portals, job forms, and websites. All conversions execute strictly inside your browser for total privacy.
                </p>

                <!-- Interactive Animated Dropzone -->
                <div id="liveDropzone" class="relative z-10 max-w-2xl mx-auto rounded-2xl border-2 border-dashed border-sky-500/50 hover:border-sky-400 bg-slate-900/80 hover:bg-slate-900/95 p-8 transition-all duration-300 cursor-pointer group overflow-hidden">
                    <div class="scanline-bar absolute inset-x-0 h-12 bg-gradient-to-b from-sky-500/10 to-transparent pointer-events-none"></div>
                    <input type="file" id="demoFileInput" class="hidden" multiple>
                    <div class="w-14 h-14 rounded-2xl bg-sky-500/15 border border-sky-500/30 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform">
                        <svg class="w-7 h-7 text-sky-400 animate-bounce" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"/>
                        </svg>
                    </div>
                    <h3 id="dropzoneStatusText" class="text-base sm:text-lg font-bold text-white mb-1 group-hover:text-sky-300 transition">
                        Drop your files here, or click to browse
                    </h3>
                    <p class="text-xs text-slate-400 mb-4">
                        Supports JPG, PNG, WebP, GIF, PDF, Word, PowerPoint & Excel • Max 100 MB each
                    </p>
                    <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-xl bg-emerald-950/60 border border-emerald-500/30 text-emerald-300 text-xs">
                        <span>🔒</span>
                        <span><strong>Client-side guaranteed:</strong> Selected files are processed locally and never sent to a server.</span>
                    </div>
                </div>
            </div>

            <!-- Select Tool Mode (15 Interactive Animated Cards) -->
            <div id="tools-section" class="space-y-5">
                <div class="flex flex-wrap items-center justify-between gap-2">
                    <div>
                        <h2 class="text-xl sm:text-2xl font-bold text-white flex items-center gap-2">
                            <span class="text-sky-400">✦</span> Select Tool Mode
                        </h2>
                        <p class="text-xs text-slate-400">Click any tool below to preview active client-side mode</p>
                    </div>
                    <span id="activeToolIndicator" class="text-xs font-mono px-3 py-1 rounded-full bg-sky-500/15 text-sky-300 border border-sky-500/30">
                        Active Mode: ↔ Resize (Custom pixels & aspect)
                    </span>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-3.5" id="toolModeGrid">
                    <!-- Populated dynamically with all 15 tools from pasted text -->
                </div>
            </div>

            <!-- Why ResizeTool Outperforms Traditional Converters -->
            <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6 sm:p-8 space-y-6">
                <div class="text-center max-w-2xl mx-auto">
                    <h2 class="text-2xl font-bold text-white">Why ResizeTool Outperforms Traditional Converters</h2>
                    <p class="text-sm text-slate-400 mt-1">Engineered from the ground up for privacy, speed, and exact compliance with upload forms.</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="bg-slate-950/80 border border-slate-800/90 hover:border-emerald-500/50 rounded-2xl p-6 transition-all duration-300 hover:-translate-y-1">
                        <div class="text-3xl mb-3 animate-float">🛡️</div>
                        <h3 class="text-base font-bold text-white mb-2">Zero-Server Privacy</h3>
                        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed">
                            Your photos, contracts, and documents never upload to a cloud server. All file parsing occurs securely in client-side memory.
                        </p>
                    </div>
                    <div class="bg-slate-950/80 border border-slate-800/90 hover:border-sky-500/50 rounded-2xl p-6 transition-all duration-300 hover:-translate-y-1">
                        <div class="text-3xl mb-3 animate-float" style="animation-delay: 0.5s;">🎯</div>
                        <h3 class="text-base font-bold text-white mb-2">Precise KB Control</h3>
                        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed">
                            Meet strict government portal limits (UPSC, SSC, US Visa) that reject files over 20KB, 50KB, or 100KB with our iterative optimizer.
                        </p>
                    </div>
                    <div class="bg-slate-950/80 border border-slate-800/90 hover:border-purple-500/50 rounded-2xl p-6 transition-all duration-300 hover:-translate-y-1">
                        <div class="text-3xl mb-3 animate-float" style="animation-delay: 1s;">⚡</div>
                        <h3 class="text-base font-bold text-white mb-2">Zero Wait Times</h3>
                        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed">
                            No waiting in server queues or dealing with file upload lags. Conversions execute instantly using your local computer processor.
                        </p>
                    </div>
                </div>
            </div>

            <!-- Targeted Online Tools & Presets -->
            <div id="all-tools-section" class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6 sm:p-8 space-y-5">
                <div>
                    <h2 class="text-xl font-bold text-white">Targeted Online Tools & Presets</h2>
                    <p class="text-xs sm:text-sm text-slate-400 mt-0.5">Quick-access routes for specific photo upload and document tasks:</p>
                </div>

                <div class="flex flex-wrap gap-2.5">
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-sky-500/50 text-xs font-semibold text-sky-300 cursor-pointer transition">🎯 Compress Image to 20KB</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-sky-500/50 text-xs font-semibold text-sky-300 cursor-pointer transition">🎯 Compress Image to 50KB</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-sky-500/50 text-xs font-semibold text-sky-300 cursor-pointer transition">🎯 Compress Image to 100KB</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-indigo-500/50 text-xs font-semibold text-indigo-300 cursor-pointer transition">↔ Image Pixel Resizer</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-indigo-500/50 text-xs font-semibold text-indigo-300 cursor-pointer transition">▣ Passport Photo Creator</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-purple-500/50 text-xs font-semibold text-purple-300 cursor-pointer transition">▤ Convert JPG to PDF</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-purple-500/50 text-xs font-semibold text-purple-300 cursor-pointer transition">⇩ PDF File Reducer</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-emerald-500/50 text-xs font-semibold text-emerald-300 cursor-pointer transition">⇄ Convert JPG to PNG</span>
                    <span class="px-3.5 py-2 rounded-xl bg-slate-950 border border-slate-800 hover:border-emerald-500/50 text-xs font-semibold text-emerald-300 cursor-pointer transition">⇄ Convert PNG to JPG</span>
                </div>

                <p class="text-xs text-slate-400">
                    Explore the full <a href="#guides-section" class="text-sky-400 underline hover:text-sky-300">practical guides</a> for step-by-step help with file preparation.
                </p>
            </div>

            <!-- Practical Guides for Images and Document Preparation -->
            <div id="guides-section" class="space-y-6">
                <div>
                    <h2 class="text-2xl font-bold text-white">Practical Guides for Images and Document Preparation</h2>
                    <p class="text-sm text-slate-400 mt-1">Detailed instructions to help you meet exact job portal, passport agency, and educational application guidelines.</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Resolution Guide -->
                    <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 space-y-3">
                        <span class="inline-block px-2.5 py-1 rounded-md text-[11px] font-bold uppercase tracking-wider bg-sky-500/15 text-sky-400 border border-sky-500/30">
                            Resolution Guide
                        </span>
                        <h3 class="text-lg font-bold text-white">Differentiating KB Limits and Pixel Dimensions</h3>
                        <p class="text-xs sm:text-sm text-slate-300 leading-relaxed">
                            A file-size limit (such as 50 KB) is fundamentally different from pixel dimensions (like 600×600 px). Resizing alters the number of pixels across the image. Compression adjusts data encoding efficiency.
                        </p>
                        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed">
                            When applying for exams or identity verifications, always input the exact required pixel width and height first under <strong>Resize</strong>, then pass it through <strong>Compress</strong> to satisfy the file-size limit.
                        </p>
                    </div>

                    <!-- Optimization -->
                    <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 space-y-3">
                        <span class="inline-block px-2.5 py-1 rounded-md text-[11px] font-bold uppercase tracking-wider bg-purple-500/15 text-purple-400 border border-purple-500/30">
                            Optimization
                        </span>
                        <h3 class="text-lg font-bold text-white">Target Size Compression Algorithm</h3>
                        <p class="text-xs sm:text-sm text-slate-300 leading-relaxed">
                            Unlike standard sliders that leave you guessing, ResizeTool uses an iterative binary search pass directly over the HTML5 Canvas image blob. It tests compression qualities from 95% down to 10% in fractions of a second to get as close to your specified KB target as technically possible.
                        </p>
                    </div>

                    <!-- Format Selection -->
                    <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 space-y-3">
                        <span class="inline-block px-2.5 py-1 rounded-md text-[11px] font-bold uppercase tracking-wider bg-emerald-500/15 text-emerald-400 border border-emerald-500/30">
                            Format Selection
                        </span>
                        <h3 class="text-lg font-bold text-white">When to Choose JPG vs PNG vs WebP</h3>
                        <ul class="space-y-2 text-xs sm:text-sm text-slate-300">
                            <li><strong class="text-white">JPEG:</strong> Best for realistic photographs and human faces. Produces smaller files with controllable lossy compression.</li>
                            <li><strong class="text-white">PNG:</strong> Best for signatures, typography, and logos where sharp edges and transparent backgrounds must not get blurry.</li>
                            <li><strong class="text-white">WebP:</strong> Delivers up to 30% smaller sizes than JPG at equivalent clarity. Recommended for fast-loading websites and modern apps.</li>
                        </ul>
                    </div>

                    <!-- Document Handling -->
                    <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 space-y-3">
                        <span class="inline-block px-2.5 py-1 rounded-md text-[11px] font-bold uppercase tracking-wider bg-amber-500/15 text-amber-400 border border-amber-500/30">
                            Document Handling
                        </span>
                        <h3 class="text-lg font-bold text-white">Optimizing PDFs Without Sacrificing Text Clarity</h3>
                        <p class="text-xs sm:text-sm text-slate-300 leading-relaxed">
                            Standard PDF compressors often degrade text into unreadable blurs. ResizeTool’s engine renders PDF pages at a calibrated 144+ DPI scale before adjusting JPEG quality, ensuring that small annotations and signatures stay crisp.
                        </p>
                    </div>
                </div>
            </div>

            <!-- Frequently Asked Questions & About / Privacy -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                
                <!-- Interactive FAQs (6 cols) -->
                <div id="faq-section" class="lg:col-span-6 bg-slate-900/80 border border-slate-800 rounded-3xl p-6 space-y-4">
                    <h2 class="text-xl font-bold text-white">Frequently Asked Questions</h2>
                    <div class="space-y-3">
                        <details class="group bg-slate-950 border border-slate-800 rounded-xl p-4 cursor-pointer" open>
                            <summary class="font-semibold text-sm text-slate-200 flex justify-between items-center list-none">
                                <span>Are my sensitive documents and photos uploaded to your server?</span>
                                <span class="text-sky-400 group-open:rotate-180 transition-transform">▼</span>
                            </summary>
                            <p class="text-xs text-slate-400 mt-2.5 leading-relaxed">
                                No. Every conversion, resize, crop, and compression happens 100% locally inside your browser using HTML5 Canvas, WebAssembly, and local Blob streams. Your files never leave your device.
                            </p>
                        </details>
                        <details class="group bg-slate-950 border border-slate-800 rounded-xl p-4 cursor-pointer">
                            <summary class="font-semibold text-sm text-slate-200 flex justify-between items-center list-none">
                                <span>How can I compress my signature or photo to under 20KB or 50KB?</span>
                                <span class="text-sky-400 group-open:rotate-180 transition-transform">▼</span>
                            </summary>
                            <p class="text-xs text-slate-400 mt-2.5 leading-relaxed">
                                Select the <strong>◉ Compress</strong> tool mode, choose your preset target (20KB, 50KB, or 100KB), and drop your image. Our iterative binary-search optimizer automatically finds the highest clarity that fits strictly below your KB limit.
                            </p>
                        </details>
                        <details class="group bg-slate-950 border border-slate-800 rounded-xl p-4 cursor-pointer">
                            <summary class="font-semibold text-sm text-slate-200 flex justify-between items-center list-none">
                                <span>Does resizing an image reduce its clarity?</span>
                                <span class="text-sky-400 group-open:rotate-180 transition-transform">▼</span>
                            </summary>
                            <p class="text-xs text-slate-400 mt-2.5 leading-relaxed">
                                Inputting your required pixel dimensions under <strong>↔ Resize</strong> first and then running <strong>◉ Compress</strong> preserves maximum sharpness for signatures, text, and facial details.
                            </p>
                        </details>
                        <details class="group bg-slate-950 border border-slate-800 rounded-xl p-4 cursor-pointer">
                            <summary class="font-semibold text-sm text-slate-200 flex justify-between items-center list-none">
                                <span>Why is this tool completely free?</span>
                                <span class="text-sky-400 group-open:rotate-180 transition-transform">▼</span>
                            </summary>
                            <p class="text-xs text-slate-400 mt-2.5 leading-relaxed">
                                Because all processing runs on your own device's CPU/GPU in client-side memory without expensive cloud processing servers, ResizeTool remains fast and free for students, job applicants, and professionals.
                            </p>
                        </details>
                    </div>
                </div>

                <!-- About ResizeTool & Privacy Policy (6 cols) -->
                <div id="about-section" class="lg:col-span-6 space-y-6">
                    <div class="bg-slate-900/80 border border-slate-800 rounded-3xl p-6 space-y-3">
                        <h2 class="text-xl font-bold text-white">About ResizeTool</h2>
                        <p class="text-xs sm:text-sm text-slate-300 leading-relaxed">
                            ResizeTool was engineered by <strong class="text-sky-400">Aditya G. Chudhari</strong> to provide students, job applicants, and professionals with a secure, zero-upload tool for preparing documents. By utilizing modern web APIs such as the HTML5 Canvas, WebAssembly, and local Blob streams, ResizeTool delivers desktop-grade utility inside your browser window.
                        </p>
                        <p class="text-xs sm:text-sm text-slate-400">
                            For questions, feature requests, or technical bug reports, reach out directly to <a href="mailto:resizetool@yahoo.com" class="text-sky-400 underline hover:text-sky-300">resizetool@yahoo.com</a>.
                        </p>
                    </div>

                    <div class="bg-slate-900/80 border border-slate-800 rounded-3xl p-6 space-y-3">
                        <div class="flex items-center justify-between">
                            <h2 class="text-lg font-bold text-white">Privacy Policy & Terms of Service</h2>
                            <span class="text-[11px] text-slate-400 font-mono">Last Updated: October 12, 2026</span>
                        </div>
                        <p class="text-xs text-slate-300 leading-relaxed">
                            <strong class="text-emerald-400">Zero File Retention:</strong> Selected images and documents are processed locally. ResizeTool does not operate an upload backend or database for storing your files.
                        </p>
                        <p class="text-xs text-slate-400 leading-relaxed">
                            <strong class="text-slate-200">Advertising & Cookies:</strong> We use Google AdSense to serve ads. Google and its third-party advertising partners may use cookies to serve ads based on your previous visits to this or other websites. You may opt out of personalized advertising by visiting Google Ads Settings or aboutads.info.
                        </p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-800/80 bg-slate-900/60 mt-12 py-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-slate-400">
            <div class="flex items-center gap-2">
                <span class="font-bold text-white">ResizeTool</span>
                <span>•</span>
                <span>© 2026 ResizeTool. Built for high performance, security, and browser privacy.</span>
            </div>
            <div class="flex flex-wrap items-center gap-4">
                <a href="#tools-section" class="hover:text-white transition">Tools</a>
                <a href="#all-tools-section" class="hover:text-white transition">All Tools</a>
                <a href="#guides-section" class="hover:text-white transition">Guides</a>
                <a href="#faq-section" class="hover:text-white transition">FAQ</a>
                <a href="#about-section" class="hover:text-white transition">About</a>
                <a href="#about-section" class="hover:text-white transition">Privacy</a>
                <a href="#about-section" class="hover:text-white transition">Terms</a>
                <a href="mailto:resizetool@yahoo.com" class="hover:text-sky-400 transition">Contact</a>
            </div>
        </div>
    </footer>

    <script>
        // --- 15 Tool Modes Data from User's Pasted Text ---
        const toolModes = [
            { icon: "↔", name: "Resize", desc: "Custom pixels & aspect" },
            { icon: "◉", name: "Compress", desc: "Target 20KB, 50KB, 100KB" },
            { icon: "✂", name: "Crop Photo", desc: "Freeform & preset ratios" },
            { icon: "⇄", name: "Format Convert", desc: "JPG, PNG, WebP" },
            { icon: "✦", name: "Photo Enhance", desc: "Brightness & contrast" },
            { icon: "▣", name: "Passport / ID", desc: "Standard photo presets" },
            { icon: "▤", name: "Image → PDF", desc: "Multi-image compile" },
            { icon: "▥", name: "Office → PDF", desc: "Word, Excel, PPT" },
            { icon: "⇩", name: "Compress PDF", desc: "Reduce document weight" },
            { icon: "▣", name: "PDF → Slides", desc: "Convert PDF to PPTX" },
            { icon: "▣", name: "Word → Slides", desc: "Generate presentations" },
            { icon: "⤢", name: "Aspect Ratio", desc: "Calculate matching dimensions" },
            { icon: "▧", name: "Print Size", desc: "Estimate inches from DPI" },
            { icon: "◉", name: "Image Details", desc: "Dimensions and color palette" },
            { icon: "✎", name: "Text Watermark", desc: "Add text and download a copy" }
        ];

        // --- Presets for the Live Animated SVG Generator ---
        const textPresets = {
            hero: `ResizeTool — 100% Private (No Uploads)
⚡ Lightning Fast WebAssembly & Canvas Engine
Free Online Image Compressor, Resizer & PDF Suite
Resize, crop & compress to 20KB, 50KB, 100KB in browser
🛡️ Zero-Server Privacy • 🎯 Precise KB Control • ⚡ Zero Wait Times
Engineered by Aditya G. Chudhari (resizetool@yahoo.com)`,
            tools: `↔ Resize (Custom pixels) • ◉ Compress (20KB, 50KB, 100KB)
✂ Crop Photo • ⇄ Format Convert (JPG, PNG, WebP) • ✦ Photo Enhance
▣ Passport / ID • ▤ Image → PDF • ▥ Office → PDF • ⇩ Compress PDF
▣ PDF → Slides • ▣ Word → Slides • ⤢ Aspect Ratio
▧ Print Size • ◉ Image Details • ✎ Text Watermark`,
            features: `Why ResizeTool Outperforms Traditional Converters
🛡️ Zero-Server Privacy: Parsed securely in client-side memory
🎯 Precise KB Control: Meet strict UPSC, SSC & US Visa limits
⚡ Zero Wait Times: Instant local WebAssembly & Canvas engine
144+ DPI Crisp PDF Compression & Iterative Binary Search`,
            full: `ResizeTool — 100% Private (No Uploads)
⚡ Lightning Fast WebAssembly & Canvas Engine
Free Online Image Compressor, Resizer & PDF Suite
Resize, crop, and compress images to custom KB limits (20KB, 50KB, 100KB)
Supports JPG, PNG, WebP, GIF, PDF, Word, PowerPoint & Excel • Max 100 MB each
↔ Resize | ◉ Compress | ✂ Crop Photo | ⇄ Format Convert | ✦ Photo Enhance
▣ Passport / ID | ▤ Image → PDF | ▥ Office → PDF | ⇩ Compress PDF
▣ PDF → Slides | ▣ Word → Slides | ⤢ Aspect Ratio | ▧ Print Size
◉ Image Details | ✎ Text Watermark
🛡️ Zero-Server Privacy • 🎯 Precise KB Control • ⚡ Zero Wait Times
Engineered by Aditya G. Chudhari • resizetool@yahoo.com • © 2026 ResizeTool`
        };

        // --- Application State ---
        const state = {
            text: textPresets.hero,
            style: "typewriter",
            lineMode: "stacked",
            fontFamily: "'Fira Code', monospace",
            fontSize: 20,
            speed: 4,
            primaryColor: "#38bdf8",
            secondaryColor: "#a855f7",
            bgColor: "#0d1117",
            transparentBg: false,
            activeTab: "full-readme" // full-readme | readme-api | svg-code
        };

        // --- Render 15 Interactive Tool Cards ---
        const toolModeGrid = document.getElementById('toolModeGrid');
        const activeToolIndicator = document.getElementById('activeToolIndicator');

        function renderToolGrid(selectedIndex = 0) {
            toolModeGrid.innerHTML = toolModes.map((tool, idx) => {
                const isSelected = idx === selectedIndex;
                return `
                    <button type="button" data-idx="${idx}" class="tool-card text-left p-4 rounded-2xl border transition-all duration-200 flex flex-col justify-between ${
                        isSelected
                            ? 'bg-sky-500/15 border-sky-400 shadow-lg shadow-sky-500/10 scale-[1.02]'
                            : 'bg-slate-900/90 border-slate-800 hover:border-slate-700 hover:bg-slate-900'
                    }">
                        <div class="flex items-center justify-between mb-2">
                            <span class="w-9 h-9 rounded-xl ${isSelected ? 'bg-sky-500 text-slate-950' : 'bg-slate-800 text-sky-400'} font-bold text-lg flex items-center justify-center transition">
                                ${tool.icon}
                            </span>
                            ${isSelected ? '<span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>' : ''}
                        </div>
                        <div>
                            <div class="font-bold text-sm text-white">${tool.name}</div>
                            <div class="text-xs text-slate-400 mt-0.5">${tool.desc}</div>
                        </div>
                    </button>
                `;
            }).join('');

            document.querySelectorAll('.tool-card').forEach(card => {
                card.addEventListener('click', () => {
                    const idx = Number(card.dataset.idx);
                    const chosen = toolModes[idx];
                    activeToolIndicator.textContent = `Active Mode: ${chosen.icon} ${chosen.name} (${chosen.desc})`;
                    renderToolGrid(idx);
                });
            });
        }
        renderToolGrid(0);

        // --- Interactive Demo Dropzone ---
        const liveDropzone = document.getElementById('liveDropzone');
        const demoFileInput = document.getElementById('demoFileInput');
        const dropzoneStatusText = document.getElementById('dropzoneStatusText');

        liveDropzone.addEventListener('click', () => demoFileInput.click());
        demoFileInput.addEventListener('change', (e) => {
            if (e.target.files && e.target.files.length > 0) {
                const f = e.target.files[0];
                const sizeKB = (f.size / 1024).toFixed(1);
                dropzoneStatusText.innerHTML = `<span class="text-emerald-400">✓ Loaded Locally: ${f.name} (${sizeKB} KB) — Ready for 100% Private Browser Processing!</span>`;
            }
        });

        // --- DOM Elements for Studio ---
        const textInput = document.getElementById('textInput');
        const lineCountBadge = document.getElementById('lineCountBadge');
        const styleButtons = document.querySelectorAll('.style-btn');
        const presetButtons = document.querySelectorAll('.preset-btn');
        const lineModeSelect = document.getElementById('lineMode');
        const fontFamilySelect = document.getElementById('fontFamily');
        const fontSizeInput = document.getElementById('fontSize');
        const fontSizeVal = document.getElementById('fontSizeVal');
        const animSpeedInput = document.getElementById('animSpeed');
        const speedVal = document.getElementById('speedVal');
        const primaryColorInput = document.getElementById('primaryColor');
        const primaryHex = document.getElementById('primaryHex');
        const secondaryColorInput = document.getElementById('secondaryColor');
        const secondaryHex = document.getElementById('secondaryHex');
        const bgColorInput = document.getElementById('bgColor');
        const transparentBgCheckbox = document.getElementById('transparentBg');
        const svgPreviewContainer = document.getElementById('svgPreviewContainer');
        const codeOutput = document.getElementById('codeOutput');
        const tabButtons = document.querySelectorAll('.code-tab');
        const tabInstruction = document.getElementById('tabInstruction');
        const copyCodeBtn = document.getElementById('copyCodeBtn');
        const copyBtnText = document.getElementById('copyBtnText');
        const copyFullReadmeBtn = document.getElementById('copyFullReadmeBtn');
        const copyFullReadmeText = document.getElementById('copyFullReadmeText');
        const downloadSvgBtn = document.getElementById('downloadSvgBtn');
        const replayBtn = document.getElementById('replayBtn');

        function escapeXml(unsafe) {
            return unsafe.replace(/[<>&'"]/g, function (c) {
                switch (c) {
                    case '<': return '&lt;';
                    case '>': return '&gt;';
                    case '&': return '&amp;';
                    case '\'': return '&apos;';
                    case '"': return '&quot;';
                }
            });
        }

        // --- Generate Self-Contained Animated SVG ---
        function generateAnimatedSVG() {
            const rawLines = state.text.split('\n').map(l => l.trim()).filter(l => l.length > 0);
            const lines = rawLines.length > 0 ? rawLines : ["ResizeTool — 100% Private (No Uploads)"];
            lineCountBadge.textContent = `${lines.length} ${lines.length === 1 ? 'Line' : 'Lines'}`;

            const fontSize = Number(state.fontSize);
            const lineHeight = Math.round(fontSize * 1.55);
            const maxChars = Math.max(...lines.map(l => l.length), 25);
            const width = Math.max(760, Math.round(maxChars * (fontSize * 0.62) + 80));
            const height = state.lineMode === 'cycle'
                ? Math.max(120, lineHeight + 64)
                : Math.max(120, lines.length * lineHeight + 56);

            const bgRect = state.transparentBg
                ? ''
                : `<rect width="100%" height="100%" rx="14" fill="${state.bgColor}" stroke="#1e293b" stroke-width="2" />`;

            let defs = '';
            let styleCss = `
                .anim-text {
                    font-family: ${state.fontFamily};
                    font-size: ${fontSize}px;
                    font-weight: 700;
                }
            `;
            let bodyElements = '';

            if (state.style === 'typewriter') {
                if (state.lineMode === 'cycle' && lines.length > 1) {
                    const totalCycle = lines.length * state.speed;
                    const slotPercent = 100 / lines.length;
                    styleCss += `
                        @keyframes cycleFade {
                            0%, 5% { opacity: 0; clip-path: inset(0 100% 0 0); }
                            15%, ${Math.max(20, slotPercent - 8)}% { opacity: 1; clip-path: inset(0 0% 0 0); }
                            ${slotPercent}%, 100% { opacity: 0; clip-path: inset(0 100% 0 0); }
                        }
                    `;
                    lines.forEach((line, idx) => {
                        const delay = (idx * state.speed).toFixed(2);
                        const yPos = Math.round(height / 2 + fontSize / 3);
                        bodyElements += `
                            <text x="50%" y="${yPos}" text-anchor="middle" fill="${state.primaryColor}" class="anim-text"
                                style="opacity:0; animation: cycleFade ${totalCycle}s infinite ${delay}s;">
                                ${escapeXml(line)}
                            </text>
                        `;
                    });
                } else {
                    styleCss += `
                        @keyframes typeReveal {
                            0% { clip-path: inset(0 100% 0 0); }
                            65%, 100% { clip-path: inset(0 0% 0 0); }
                        }
                    `;
                    lines.forEach((line, idx) => {
                        const yPos = 40 + idx * lineHeight;
                        const delay = (idx * 0.45).toFixed(2);
                        bodyElements += `
                            <text x="32" y="${yPos}" fill="${idx % 2 === 0 ? state.primaryColor : state.secondaryColor}" class="anim-text"
                                style="clip-path: inset(0 100% 0 0); animation: typeReveal ${state.speed}s steps(45, end) infinite alternate ${delay}s;">
                                ${escapeXml(line)}
                            </text>
                        `;
                    });
                }
            } else if (state.style === 'gradient') {
                defs = `
                    <linearGradient id="flowGrad" x1="0%" y1="0%" x2="200%" y2="0%">
                        <stop offset="0%" stop-color="${state.primaryColor}" />
                        <stop offset="50%" stop-color="${state.secondaryColor}" />
                        <stop offset="100%" stop-color="${state.primaryColor}" />
                        <animate attributeName="x1" values="0%;-100%" dur="${state.speed}s" repeatCount="indefinite" />
                        <animate attributeName="x2" values="200%;100%" dur="${state.speed}s" repeatCount="indefinite" />
                    </linearGradient>
                `;
                styleCss += `
                    @keyframes floatWave {
                        0%, 100% { transform: translateY(0px); }
                        50% { transform: translateY(-4px); }
                    }
                `;
                lines.forEach((line, idx) => {
                    const yPos = state.lineMode === 'cycle'
                        ? Math.round(height / 2 + fontSize / 3)
                        : 42 + idx * lineHeight;
                    const delay = (idx * 0.25).toFixed(2);
                    bodyElements += `
                        <text x="50%" y="${yPos}" text-anchor="middle" fill="url(#flowGrad)" class="anim-text"
                            style="animation: floatWave ${state.speed}s ease-in-out infinite ${delay}s;">
                            ${escapeXml(line)}
                        </text>
                    `;
                });
            } else if (state.style === 'neon') {
                defs = `
                    <filter id="neonGlow" x="-20%" y="-20%" width="140%" height="140%">
                        <feGaussianBlur stdDeviation="3.5" result="blur1" />
                        <feGaussianBlur stdDeviation="8" result="blur2" />
                        <feMerge>
                            <feMergeNode in="blur2" />
                            <feMergeNode in="blur1" />
                            <feMergeNode in="SourceGraphic" />
                        </feMerge>
                    </filter>
                `;
                styleCss += `
                    @keyframes neonFlicker {
                        0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% { opacity: 1; }
                        20%, 24%, 55% { opacity: 0.45; }
                    }
                `;
                lines.forEach((line, idx) => {
                    const yPos = state.lineMode === 'cycle'
                        ? Math.round(height / 2 + fontSize / 3)
                        : 42 + idx * lineHeight;
                    const color = idx % 2 === 0 ? state.primaryColor : state.secondaryColor;
                    bodyElements += `
                        <text x="50%" y="${yPos}" text-anchor="middle" fill="${color}" filter="url(#neonGlow)" class="anim-text"
                            style="animation: neonFlicker ${state.speed}s infinite ${idx * 0.35}s;">
                            ${escapeXml(line)}
                        </text>
                    `;
                });
            } else if (state.style === 'glitch') {
                styleCss += `
                    @keyframes glitchShiftA {
                        0%, 100% { transform: translate(0, 0); }
                        20% { transform: translate(-3px, 1px); }
                        40% { transform: translate(3px, -1px); }
                        60% { transform: translate(-2px, -1px); }
                        80% { transform: translate(2px, 2px); }
                    }
                    @keyframes glitchShiftB {
                        0%, 100% { transform: translate(0, 0); }
                        25% { transform: translate(3px, -1px); }
                        50% { transform: translate(-3px, 2px); }
                        75% { transform: translate(2px, -2px); }
                    }
                `;
                lines.forEach((line, idx) => {
                    const yPos = state.lineMode === 'cycle'
                        ? Math.round(height / 2 + fontSize / 3)
                        : 42 + idx * lineHeight;
                    const safeLine = escapeXml(line);
                    bodyElements += `
                        <g>
                            <text x="50%" y="${yPos}" text-anchor="middle" fill="${state.secondaryColor}" opacity="0.75" class="anim-text"
                                style="animation: glitchShiftA ${Math.max(0.8, state.speed / 3)}s infinite;">
                                ${safeLine}
                            </text>
                            <text x="50%" y="${yPos}" text-anchor="middle" fill="${state.primaryColor}" opacity="0.75" class="anim-text"
                                style="animation: glitchShiftB ${Math.max(0.9, state.speed / 2.5)}s infinite;">
                                ${safeLine}
                            </text>
                            <text x="50%" y="${yPos}" text-anchor="middle" fill="#ffffff" class="anim-text">
                                ${safeLine}
                            </text>
                        </g>
                    `;
                });
            }

            return `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 ${width} ${height}" width="100%" height="${height}">
  <defs>${defs}
    <style>${styleCss}</style>
  </defs>
  ${bgRect}
  ${bodyElements}
</svg>`;
        }

        // --- Generate Instant Typing SVG URL for GitHub ---
        function generateTypingSvgUrl() {
            const rawLines = state.text.split('\n').map(l => l.trim()).filter(l => l.length > 0);
            const lines = rawLines.length > 0 ? rawLines : ["ResizeTool — 100% Private (No Uploads)"];
            const encodedLines = lines.map(l => encodeURIComponent(l)).join(';');
            const colorHex = state.primaryColor.replace('#', '');
            const durationMs = Math.round(state.speed * 950);
            const fontName = state.fontFamily.includes('Fira') ? 'Fira+Code' : (state.fontFamily.includes('Orbitron') ? 'Orbitron' : 'Inter');
            return `https://readme-typing-svg.demolab.com?font=${fontName}&weight=700&size=${state.fontSize}&duration=${durationMs}&pause=900&color=${colorHex}&center=true&vCenter=true&multiline=false&width=860&height=55&lines=${encodedLines}`;
        }

        // --- Generate Complete Ready-to-Paste GitHub README.md containing ALL Pasted Text ---
        function generateCompleteGitHubReadme() {
            const typingUrl = generateTypingSvgUrl();
            return `<div align="center">

# ⚡ ResizeTool — 100% Private (No Uploads)

<!-- Live Animated Typing SVG Banner -->
<p align="center">
  <img src="${typingUrl}" alt="ResizeTool Animated Typing Banner" />
</p>

<!-- Live Status Badges -->
<p align="center">
  <img src="https://img.shields.io/badge/Privacy-100%25_Client--Side_(No_Uploads)-10b981?style=for-the-badge&logo=shield&logoColor=white" alt="100% Private" />
  <img src="https://img.shields.io/badge/Engine-WebAssembly_%26_HTML5_Canvas-38bdf8?style=for-the-badge&logo=webassembly&logoColor=white" alt="WebAssembly Engine" />
  <img src="https://img.shields.io/badge/Target_KB-20KB_%7C_50KB_%7C_100KB-a855f7?style=for-the-badge" alt="Target KB" />
  <img src="https://img.shields.io/badge/Max_File_Size-100_MB_Each-f59e0b?style=for-the-badge" alt="Max 100MB" />
</p>

### **Free Online Image Compressor, Resizer & PDF Suite**
Resize, crop, and compress images to custom KB limits (**20KB, 50KB, 100KB**) for official exam portals, job forms, and websites. All conversions execute strictly inside your browser for total privacy.

> 🔒 **Client-side guaranteed:** Selected files are processed locally and never sent to a server.  
> 📂 **Supported Formats:** JPG, PNG, WebP, GIF, PDF, Word, PowerPoint & Excel • *Max 100 MB each*

</div>

---

## 🛠️ Select Tool Mode (All 15 Client-Side Tools)

| Icon | Tool Mode | Capability & Description |
| :---: | :--- | :--- |
| **↔** | **Resize** | Custom pixels & aspect |
| **◉** | **Compress** | Target 20KB, 50KB, 100KB |
| **✂** | **Crop Photo** | Freeform & preset ratios |
| **⇄** | **Format Convert** | JPG, PNG, WebP |
| **✦** | **Photo Enhance** | Brightness & contrast |
| **▣** | **Passport / ID** | Standard photo presets |
| **▤** | **Image → PDF** | Multi-image compile |
| **▥** | **Office → PDF** | Word, Excel, PPT |
| **⇩** | **Compress PDF** | Reduce document weight |
| **▣** | **PDF → Slides** | Convert PDF to PPTX |
| **▣** | **Word → Slides** | Generate presentations |
| **⤢** | **Aspect Ratio** | Calculate matching dimensions |
| **▧** | **Print Size** | Estimate inches from DPI |
| **◉** | **Image Details** | Dimensions and color palette |
| **✎** | **Text Watermark** | Add text and download a copy |

---

## 🚀 Why ResizeTool Outperforms Traditional Converters
*Engineered from the ground up for privacy, speed, and exact compliance with upload forms.*

- 🛡️ **Zero-Server Privacy:** Your photos, contracts, and documents never upload to a cloud server. All file parsing occurs securely in client-side memory.
- 🎯 **Precise KB Control:** Meet strict government portal limits (UPSC, SSC, US Visa) that reject files over 20KB, 50KB, or 100KB with our iterative optimizer.
- ⚡ **Zero Wait Times:** No waiting in server queues or dealing with file upload lags. Conversions execute instantly using your local computer processor.

---

## 🎯 Targeted Online Tools & Presets
Quick-access routes for specific photo upload and document tasks:

\`Compress Image to 20KB\` • \`Compress Image to 50KB\` • \`Compress Image to 100KB\` • \`Image Pixel Resizer\` • \`Passport Photo Creator\` • \`Convert JPG to PDF\` • \`PDF File Reducer\` • \`Convert JPG to PNG\` • \`Convert PNG to JPG\`

---

## 📚 Practical Guides for Images and Document Preparation
*Detailed instructions to help you meet exact job portal, passport agency, and educational application guidelines.*

### 1. Resolution Guide — Differentiating KB Limits and Pixel Dimensions
A file-size limit (such as 50 KB) is fundamentally different from pixel dimensions (like 600×600 px). Resizing alters the number of pixels across the image. Compression adjusts data encoding efficiency.

When applying for exams or identity verifications, always input the exact required pixel width and height first under **Resize**, then pass it through **Compress** to satisfy the file-size limit.

### 2. Optimization — Target Size Compression Algorithm
Unlike standard sliders that leave you guessing, ResizeTool uses an iterative binary search pass directly over the HTML5 Canvas image blob. It tests compression qualities from 95% down to 10% in fractions of a second to get as close to your specified KB target as technically possible.

### 3. Format Selection — When to Choose JPG vs PNG vs WebP
- **JPEG:** Best for realistic photographs and human faces. Produces smaller files with controllable lossy compression.
- **PNG:** Best for signatures, typography, and logos where sharp edges and transparent backgrounds must not get blurry.
- **WebP:** Delivers up to 30% smaller sizes than JPG at equivalent clarity. Recommended for fast-loading websites and modern apps.

### 4. Document Handling — Optimizing PDFs Without Sacrificing Text Clarity
Standard PDF compressors often degrade text into unreadable blurs. ResizeTool’s engine renders PDF pages at a calibrated 144+ DPI scale before adjusting JPEG quality, ensuring that small annotations and signatures stay crisp.

---

## ❓ Frequently Asked Questions (Interactive Collapsible)

<details>
<summary><b>Are my sensitive documents and photos uploaded to your server?</b></summary>
<br/>
No. Selected images and documents are processed 100% locally inside your browser using HTML5 Canvas, WebAssembly, and local Blob streams. ResizeTool does not operate an upload backend or database for storing your files.
</details>

<details>
<summary><b>How can I compress my signature or photo to under 20KB or 50KB?</b></summary>
<br/>
Select the <b>◉ Compress</b> tool mode, choose your target KB limit (20KB, 50KB, or 100KB), and ResizeTool's iterative binary search algorithm will automatically optimize the image blob to land right below your target size.
</details>

<details>
<summary><b>Does resizing an image reduce its clarity?</b></summary>
<br/>
Always input the exact required pixel width and height first under <b>Resize</b>, then pass it through <b>Compress</b> to satisfy the file-size limit while preserving maximum sharpness.
</details>

<details>
<summary><b>Why is this tool completely free?</b></summary>
<br/>
Because all conversions execute locally using your own device processor without cloud server queues, ResizeTool provides desktop-grade utility completely free.
</details>

---

## 👨‍💻 About ResizeTool & Privacy Policy

**ResizeTool** was engineered by **Aditya G. Chudhari** to provide students, job applicants, and professionals with a secure, zero-upload tool for preparing documents. By utilizing modern web APIs such as the HTML5 Canvas, WebAssembly, and local Blob streams, ResizeTool delivers desktop-grade utility inside your browser window.

📧 **Contact:** For questions, feature requests, or technical bug reports, reach out directly to [resizetool@yahoo.com](mailto:resizetool@yahoo.com).

### Privacy Policy & Terms of Service
*Last Updated: October 12, 2026.*
- **Zero File Retention:** Selected images and documents are processed locally. ResizeTool does not operate an upload backend or database for storing your files.
- **Advertising & Cookies:** We use Google AdSense to serve ads. Google and its third-party advertising partners may use cookies to serve ads based on your previous visits to this or other websites. You may opt out of personalized advertising by visiting Google Ads Settings or aboutads.info.

---
<p align="center">
  <b>© 2026 ResizeTool.</b> Built for high performance, security, and browser privacy.
</p>`;
        }

        // --- Render Everything ---
        function renderAll() {
            const svgCode = generateAnimatedSVG();
            svgPreviewContainer.innerHTML = svgCode;

            if (state.activeTab === 'full-readme') {
                tabInstruction.innerHTML = `⚡ <strong>Complete GitHub README.md (Direct Paste):</strong> Copy & paste this directly into your GitHub <code>README.md</code> — includes the animated typing banner, all 15 tools, guides, collapsible FAQs, and credits!`;
                codeOutput.textContent = generateCompleteGitHubReadme();
            } else if (state.activeTab === 'readme-api') {
                const url = generateTypingSvgUrl();
                tabInstruction.innerHTML = `⚡ <strong>Animated Typing Header Markdown:</strong> Paste this snippet anywhere in your GitHub <code>README.md</code> for a live cycling typewriter banner!`;
                codeOutput.textContent = `<!-- Paste directly into GitHub README.md -->\n<p align="center">\n  <img src="${url}" alt="ResizeTool Animated Banner" />\n</p>`;
            } else {
                tabInstruction.innerHTML = `🎨 <strong>Pure Animated SVG Code:</strong> Click "Download resizetool-animated.svg" above or copy this SVG code into your repository and embed it via <code>![ResizeTool](./resizetool-animated.svg)</code>.`;
                codeOutput.textContent = svgCode;
            }
        }

        // --- Event Listeners ---
        textInput.addEventListener('input', (e) => {
            state.text = e.target.value;
            renderAll();
        });

        presetButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                presetButtons.forEach(b => {
                    b.classList.remove('bg-indigo-600', 'text-white');
                    b.classList.add('bg-slate-800', 'text-slate-300');
                });
                btn.classList.remove('bg-slate-800', 'text-slate-300');
                btn.classList.add('bg-indigo-600', 'text-white');
                const key = btn.dataset.preset;
                state.text = textPresets[key];
                textInput.value = state.text;
                renderAll();
            });
        });

        styleButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                styleButtons.forEach(b => {
                    b.classList.remove('bg-indigo-600/20', 'border-indigo-500', 'text-white');
                    b.classList.add('border-slate-800', 'bg-slate-900/60', 'text-slate-300');
                });
                btn.classList.remove('border-slate-800', 'bg-slate-900/60', 'text-slate-300');
                btn.classList.add('bg-indigo-600/20', 'border-indigo-500', 'text-white');
                state.style = btn.dataset.style;
                renderAll();
            });
        });

        lineModeSelect.addEventListener('change', (e) => {
            state.lineMode = e.target.value;
            renderAll();
        });

        fontFamilySelect.addEventListener('change', (e) => {
            state.fontFamily = e.target.value;
            renderAll();
        });

        fontSizeInput.addEventListener('input', (e) => {
            state.fontSize = e.target.value;
            fontSizeVal.textContent = `${e.target.value}px`;
            renderAll();
        });

        animSpeedInput.addEventListener('input', (e) => {
            state.speed = e.target.value;
            speedVal.textContent = `${e.target.value}s`;
            renderAll();
        });

        primaryColorInput.addEventListener('input', (e) => {
            state.primaryColor = e.target.value;
            primaryHex.textContent = e.target.value.toUpperCase();
            renderAll();
        });

        secondaryColorInput.addEventListener('input', (e) => {
            state.secondaryColor = e.target.value;
            secondaryHex.textContent = e.target.value.toUpperCase();
            renderAll();
        });

        bgColorInput.addEventListener('input', (e) => {
            state.bgColor = e.target.value;
            renderAll();
        });

        transparentBgCheckbox.addEventListener('change', (e) => {
            state.transparentBg = e.target.checked;
            renderAll();
        });

        tabButtons.forEach(tab => {
            tab.addEventListener('click', () => {
                tabButtons.forEach(t => {
                    t.classList.remove('bg-indigo-600', 'text-white');
                    t.classList.add('text-slate-400');
                });
                tab.classList.remove('text-slate-400');
                tab.classList.add('bg-indigo-600', 'text-white');
                state.activeTab = tab.dataset.tab;
                renderAll();
            });
        });

        replayBtn.addEventListener('click', () => renderAll());

        function copyTextToClipboard(text, feedbackElem, successLabel) {
            const orig = feedbackElem.textContent;
            const fallbackCopy = () => {
                const ta = document.createElement('textarea');
                ta.value = text;
                document.body.appendChild(ta);
                ta.select();
                document.execCommand('copy');
                document.body.removeChild(ta);
            };
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(text).catch(fallbackCopy);
            } else {
                fallbackCopy();
            }
            feedbackElem.textContent = successLabel;
            setTimeout(() => { feedbackElem.textContent = orig; }, 2200);
        }

        copyCodeBtn.addEventListener('click', () => {
            copyTextToClipboard(codeOutput.textContent, copyBtnText, "✓ Copied! Ready to Paste in GitHub");
        });

        copyFullReadmeBtn.addEventListener('click', () => {
            copyTextToClipboard(generateCompleteGitHubReadme(), copyFullReadmeText, "✓ Complete GitHub README.md Copied!");
        });

        downloadSvgBtn.addEventListener('click', () => {
            const svgString = generateAnimatedSVG();
            const blob = new Blob([svgString], { type: 'image/svg+xml;charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'resizetool-animated.svg';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        });

        // Initial Render
        renderAll();
    </script>
</body>
</html>
