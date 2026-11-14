# 🚀 Agent Skills Hub
### Modular Agentic Design & Engineering Skill Library for AI Coding Agents
**Author:** [Shahin Karimov](https://github.com/shahinjk-cpu) · **Standard:** Antigravity / Claude Code / Cursor `SKILL.md`

`agent-skills-hub` süni intellekt agentləri (**Google Antigravity, Claude Code, Cursor, v0, Lovable**) üçün hazırlanmış modul, peşəkar dizayn, memarlıq və mühəndislik bacarıqları kitabxanasıdır.

Hər bir qovluq AI-ın şablon və keyfiyyətsiz ("AI-slop") kod yazmasının qarşısını alan, production səviyyəli standartları məcburi tətbiq edən dəqiq təlimat faylından (`SKILL.md`) ibarətdir.

---

## 📂 Kitabxananın Strukturu

```text
agent-skills-hub/
│
├── 🌐 core/                              # HƏR BİR LAYİHƏDƏ MƏCBURİ OLAN DİZAYN VƏ QA NÜVƏSİ
│   ├── taste-skill/                     # "AI-slop" qadağası, unikal editorial estetika
│   ├── ui-ux-pro-max/                   # 8pt grid, konsentrik radiuslar, OKLCH rəng sistemi
│   ├── frontend-design/                 # Bento-grid tərtibatı, təmiz semantik HTML & Tailwind
│   ├── a11y-auditing/                   # WCAG 2.2 AA əlçatanlıq, kontrast və klaviatura naviqasiyası
│   └── design-review/                   # Mobile 375px → 4K çoxölçülü responsiv vizual QA
│
└── 📦 presets/                          # SAHƏLƏRƏ VƏ LAYİHƏ NÖVLƏRİNƏ GÖRƏ İXTİSASLAŞMIŞ PAKETLƏR
    │
    ├── 🎓 elearning/                    # ONLINE TƏLİM VƏ LMS PLATFORMALARI PAKETİ
    │   ├── clean-architecture-dotnet/   # .NET 10 Service-Layer, Repository & Unit of Work, Result Pattern
    │   ├── questpdf-vector-design/      # 300 DPI A4 qızılı vektor sertifikat, gilloş və QR kod
    │   ├── proctoring-signalr-vision/   # MediaPipe brauzer baxışı və SignalR Core real-vaxt imtahan nəzarəti
    │   ├── socratic-ai-rag/             # Gemini API ilə dərs transkriptinə bağlı Sokratik AI köməkçi
    │   ├── threejs-3d/                  # 3D sertifikat tilt parıltısı və interaktiv WebGL nüvəsi
    │   ├── gsap-framer-scroll-animation/# Duolingo tərzi Streak alovu, XP sayğacı və mikro-interaksiyalar
    │   └── web-design-guidelines/       # "Zen / Focus mode" və diqqət dağıtmayan dərs oxuma erqonomikası
    │
    └── 🎮 3d-game-development/          # 3D MODELLİ VEB OYUNLAR PAKETİ (THREE.JS / WEBGL)
        ├── threejs-game-loop/           # Delta-time oyun dövrü, WASD, 360° PointerLock və 3rd person kamera
        ├── physics-engine-rapier/       # Rapier3D WASM fizika, qravitasiya, toqquşmalar və tətikçilər
        ├── gltf-character-animation/    # Draco .glb modellər, skelet animasiya keçidləri (crossFadeTo)
        ├── glsl-shaders-particles/      # Fərdiləşdirilmiş güc qalxanları, lazerlər və GPU zərrəcikləri
        ├── spatial-audio-3d/            # Üçölçülü məkan səsi, addım səsləri və məsafəyə görə zəifləmə
        └── 3d-game-optimization/        # InstancedMesh, 60 FPS büdcəsi və GPU yaddaş təmizliyi (dispose)

    │
    └── ⚡ agentic-ecosystem/            # AVTONOM AI, MCP & SELF-HOSTED EKOSİSTEMİ (55 SKILL)
        ├── bmad-method/                 # Breakthrough Agile AI — PM, Memar, Dev, QA multi-agent bölgüsü
        ├── karpathy-skills/             # Andrej Karpathy minimalizm, sıfır fərziyyə və sıfır bloat prinsipləri
        ├── gsd/                         # Get Shit Done (GSD) — Spekifikasiyalı icra və kontekst qorunması
        ├── claudex-loop/                # Ralph/Claude avtonom özünü təshih edən rekursiv agent dövrü
        ├── swarmchat/                   # Çoxagentli swarm ortaq lövhəsi, səsvermə və konsensus protokolu
        ├── boeing-manual-style/         # ASD-STE100 Texniki İngilis dili — sıfır boşboğazlıq, dəqiq təlimatlar
        ├── design-extract/              # Manavarya09/design-extract — DOM-dan W3C və Tailwind token çıxarılması
        ├── inspo-mcp/                   # Canlı veb sayt referanslarını oxuyan dizayn ilhamı MCP serveri
        ├── bencho-dev/                  # Bencho.dev interaktiv Framer Motion mikro-interaksiyaları
        ├── uiverse/                     # UIverse.io açıq mənbəli CSS/Tailwind zəngin element kitabxanası
        ├── transitions-dev/             # Transitions.dev CSS View Transitions və axıcı səhifə morfizmi
        ├── ha-mcp/                      # Home Assistant MCP serveri ilə təbii dildə ağıllı ev nəzarəti
        ├── context7/                    # Versiyaya uyğun rəsmi kitabxana sənədlərini kontekstə çəkən MCP
        ├── sentry/                      # Sentry real-vaxt xəta diaqnostikası və stek izi təhlili
        ├── playwright-cli/              # Yüksək dayanıqlı Playwright brauzer avtomatlaşdırması və vizual test
        ├── treejs-game-skill/           # 3D Three.js brauzer oyunu üçün tam fizika, kamera və dövr mühərriki
        ├── img2threejs/                 # 2D təsvirləri və mockupları interaktiv 3D WebGL səhnələrinə çevirmə
        ├── ssd-moe-engine/              # 70B-405B MoE modellərini NVMe SSD-dən axınla işlətmə bələdçisi
        ├── claude-make-an-anime/        # Çoxkadrli anime ardıcıllığı, xarakter vərəqələri və səhnə rejissoru
        ├── ppt-master/                  # Apple Keynote səviyyəsində 16:9 geniş ekranlı peşəkar təqdimat dizaynı
        ├── film-studio-skills/          # Kino ssenarisi, 3 nöqtəli işıqlandırma, kadr bucaqları və Foley audio
        ├── understand-anything/         # Feynman metodu ilə mürəkkəb kod bazalarını ilk prinsiplərdən anlama
        ├── matt-pocock-skills/          # Matt Pocock Type-Level TypeScript və Zod sxem mühəndisliyi
        ├── invidious/                   # İzləməsiz və API kvotasız YouTube axtarışı və transkript çıxarılması
        ├── localsend/                   # Şəbəkə daxilində cihazlararası LocalSend protokolu ilə fayl paylaşımı
        ├── stirling-pdf/                # Self-hosted Stirling-PDF ilə lokal PDF birləşdirmə, OCR və təmizləmə
        ├── immich/                      # Immich foto/video arxivi, semantik CLIP axtarışı və üz tanıma API-si
        ├── we-promise-sure/             # Sure (Maybe Finance) şəxsi büdcə və maliyyə hesabatı platforması
        ├── haven/                       # Ev şəbəkəsində məxfi lokal LLM serveri və fərdi agent habı
        ├── opencode-manager/            # OpenCode agentlərinin git worktree-lərdə təcrid olunmuş sessiya paneli
        ├── isponsorblocktv/             # Apple TV və smart TV-lərdə YouTube sponsor bloklarını avtomatik ötürmə
        ├── zapfast/                     # Yüksək performanslı ultra-yüngül (150MB) yerli Rust WhatsApp müştərisi
        ├── pdf-craft/                   # Paged Media və Typst ilə nəşriyyat keyfiyyətində sənəd tərtibatı
        ├── pi-alert/                    # Lokal şəbəkəyə qoşulan yeni cihazları aşkarlayan təhlükəsizlik keşikçisi
        ├── pangolin/                    # Identity-aware təhlükəsiz tərs proksi və internet tunelləri
        ├── phosphene/                   # Vizual sintezator, audio-reaktiv qrafika və GLSL şeyderləri
        ├── open-generative-ai/          # Açıq çəkili təməl modellərinin yerli yerləşdirilmə bələdçisi
        ├── openseo/                     # Core Web Vitals və JSON-LD sxemli texniki axtarış optimizasiyası
        ├── appflowy/                    # AppFlowy yerli Notion alternativi, cədvəllər və qeydlər ekosistemi
        ├── openproject/                 # OpenProject Gantt yol xəritələri və çevik tapşırıq idarəetməsi
        ├── cal-diy/                     # Cal.com self-hosted şəxsi görüş təqvimi və webhook avtomatlaşdırması
        ├── apkstart/                    # Android APK dekompilyasiyası, manifest analizi və sideload alətləri
        ├── univer/                      # Google Sheets/Docs alternativi kətan üzərində ofis mühərriki
        ├── anydoc/                      # PDF, DOCX, Markdown və XLSX arasında universal format konvertoru
        ├── archify/                     # C4 arxitektura diaqramları və sistem dizayn sənədləşməsi
        ├── orca/                        # Addım-addım mühakimə zənciri və 3D kəsmə (slicing) avtomatlaşdırması
        ├── basemode/                    # Editorial minimalist dizayn sistemi və neytral tipoqrafiya
        ├── doop/                        # Bəyannaməli verilənlər təkrarının aradan qaldırılması (deduplication)
        ├── nota/                        # Texniki müəlliflər üçün diqqət dağıtmayan lokal qeyd sistemi
        ├── career-ops/                  # ATS-optimallaşdırılmış CV, motivasiya məktubu və STAR müsahibə hazırlığı
        ├── 500-ai-agents-projects/      # 500+ süni intellekt agenti layihəsi və arxitektura nümunələri
        └── billion-context/             # Nəhəng kontekst pəncərələrinin strateji idarəetmə metodologiyası
```

---

## ⚡ İstənilən Yeni Layihədə İstifadə Qaydası

### 1. AI Agenti ilə (Prompt Üsulu)
Yeni bir layihə qovluğunda AI agentinizə sadəcə bu təlimatı verin:

> *"Mən yeni bir layihə qururam. Zəhmət olmasa `https://github.com/shahinjk-cpu/agent-skills-hub` reposundan `core/` qovluğunu və uyğun `presets/` qovluğunu cari layihənin `.agents/skills/` qovluğuna kopyala və işə başla."*

### 2. Tək Sətirlik Terminal Əmri ilə (`degit` / `git`)
Layihə qovluğunuzda terminalı açın və istədiyiniz paketi birbaşa layihəyə çəkin:

```bash
# Əsas dizayn nüvəsini çəkmək:
npx degit shahinjk-cpu/agent-skills-hub/core .agents/skills/

# E-learning paketini əlavə etmək:
npx degit shahinjk-cpu/agent-skills-hub/presets/elearning .agents/skills/

# 3D Oyun paketini əlavə etmək:
npx degit shahinjk-cpu/agent-skills-hub/presets/3d-game-development .agents/skills/
```

---

## 📜 Lisenziya
Bu repozitoriya açıq mənbəlidir (MIT License) və sərbəst şəkildə istənilən kommersiya və ya təhsil layihəsində istifadə edilə bilər.
