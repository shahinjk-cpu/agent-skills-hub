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
