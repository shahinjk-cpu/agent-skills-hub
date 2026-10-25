# 🎮 3D Game Development Skills Preset (Web & Three.js)

Bu qovluq brauzerdə **3D modelli, real-vaxt fizikalı və animasiyalı oyunlar** hazırlamaq üçün tələb olunan bütün mühəndislik və dizayn bacarıqlarını özündə cəmləşdirən xüsusi preset-dir.

---

## 📦 Paketə Daxil Olan 6 Əsas Skill:

| Skill | Adı və Rolu | Nə Üçün Lazımdır? |
|---|---|---|
| 🎮 **`threejs-game-loop`** | Oyun dövrü, Giriş (WASD/Mouse) və Kamera | Delta-time, Pointer Lock (360° maus nəzarəti), 3rd/1st person kamera izləməsi. |
| ⚡ **`physics-engine-rapier`** | 3D Fizika Mühərriki (Rapier WASM) | Qravitasiya, toqquşmalar (colliders), pilləkən qalxma, tullanma və tətikçilər (coin triggers). |
| 🏃 **`gltf-character-animation`** | Model və Skelet Animasiyası | `.glb` yüklənməsi (Draco), Idle → Run → Jump animasiya keçidləri (`crossFadeTo`), ələ silah taxılması. |
| ✨ **`glsl-shaders-particles`** | GLSL Shader-lər və Zərrəcik Effektləri | Enerji qalxanları, lazerlər, partlayış və qığılcım zərrəcikləri (GPU particles), Bloom post-processing. |
| 🔊 **`spatial-audio-3d`** | 3D Məkan Səsi (Spatial Audio) | Kameraya görə sağdan/soldan eşidilən mənbə səsləri (ocaq səsi, addım səsi, məsafəyə görə zəifləmə). |
| 🚀 **`3d-game-optimization`** | 60 FPS Optimizasiya və Yaddaş Təmizliyi | `InstancedMesh` (1 draw call ilə 5000 ağac), LOD (məsafəyə görə keyfiyyət), `dispose()` ilə yaddaş sızması qadağası. |

---

## 🚀 Sabah 3D Oyun Layihəsinə Necə Qoşmaq Olar?

### Üsul 1: AI Agentə Prompt ilə
Yeni bir 3D oyun layihəsi açdığınız zaman agentə sadəcə bu təlimatı verin:
> *"Mən yeni bir 3D veb oyunu hazırlayıram. Zəhmət olmasa mənim `skills-presets/3d-game-development/` qovluğundakı bütün skill-ləri layihənin `.agents/skills/` qovluğuna kopyala və oyunu həmin arxitektura əsasında qurmağa başla."*

### Üsul 2: Terminal Əmri ilə
```powershell
Copy-Item -Path "skills-presets\3d-game-development\*" -Destination ".agents\skills\" -Recurse -Force
```
