---
name: questpdf-vector-design
description: >-
  Design and render high-fidelity, 300 DPI vector PDF certificates, diplomas, and documents
  using QuestPDF in C#. Use when generating certificates, invoices, or dynamic PDF reports.
---

# QuestPDF Vector Certificate & Document Design

This skill provides layout rules, typography guidelines, and vector decoration standards for creating world-class, print-ready (300 DPI) PDF certificates using **QuestPDF**.

## 1. Document Layout & Canvas Setup
- **Page Format:** A4 Landscape (`PageSizes.A4.Landscape()`).
- **Margins:** 0 margins on page setup, handled internally via padded containers to allow full-bleed background fills.
- **Color Palette (Golden Ivory Luxury):**
  - Background Canvas: Warm Ivory (`#FDFBF7`) with subtle vector watermarks.
  - Metallic Gold Accents: `#B8860B` (Dark Goldenrod) → `#FFD700` (Gold) → `#DAA520` (Goldenrod) → `#8B6914`.
  - Primary Text: Deep Charcoal `#1A1A1A` (never pure black `#000000`).
  - Secondary Text: Warm Gray `#555555`.

## 2. Guilloche Border & Security Elements
- **Banknote Guilloche Frame:** Dual-layered geometric vector border (outer 4pt gold line + inner 1pt intricate dashed/flourish border).
- **Embossed Golden Seal:** Circular vector medallion featuring the KurSiv insignia, graduation year (`2026`), and Latin motto.
- **Dynamic QR Code:** Render a 120x120px QR code using SkiaSharp / QRCoder linking to `https://kursiv.az/verify/{serial}`.
- **Cryptographic Footprint:** Include the formatted Serial (`KRS-2026-XXXX-XXXX`) and truncated SHA-256 hash at the bottom edge.

## 3. Typography & Multi-language Support
- Use high-contrast serif typography for recipient name: **Cormorant Garamond** or **Playfair Display** (32pt - 40pt).
- Subheadings and metadata in clean sans-serif (**Inter** or **Plus Jakarta Sans**, 10pt - 14pt).
- **Azerbaijani Diacritic Support:** Ensure all Azerbaijani characters (`ə`, `ı`, `ğ`, `ö`, `ş`, `ü`, `İ`) are fully supported by embedding TTF font files into the QuestPDF font manager.

## 4. QuestPDF Fluent Implementation Pattern
```csharp
public class CertificateDocument(CertificateModel model) : IDocument
{
    public DocumentMetadata GetMetadata() => DocumentMetadata.Default;
    public void Compose(IDocumentContainer container)
    {
        container.Page(page =>
        {
            page.Size(PageSizes.A4.Landscape());
            page.Margin(20);
            page.Content().Border(3).BorderColor("#DAA520").Padding(20).Column(col =>
            {
                col.Item().AlignCenter().Text("KurSiv LMS").FontSize(28).SemiBold().FontColor("#B8860B");
                col.Item().AlignCenter().Text("SERTİFİKAT").FontSize(36).Bold().FontColor("#1A1A1A");
                col.Item().PaddingVertical(15).AlignCenter().Text(model.RecipientName).FontSize(30).FontFamily("Cormorant Garamond");
                col.Item().AlignCenter().Text($"uğurla başa vurdu: {model.CourseTitle}").FontSize(16);
            });
        });
    }
}
```
