# Image Filters — egui Sliders

Episode 14 of the **Learn egui in Neovim** series.

An image filters app with sliders for brightness, contrast, saturation, and blur, showing a live color preview that reflects the applied adjustments.

## What You'll Learn

- `egui::Slider::new()` with a range and `.suffix()` for units
- `ui.add()` to insert slider widgets into the layout
- Applying brightness, contrast, and saturation math to compute a preview color
- `ui.allocate_exact_size()` and `ui.painter().rect_filled()` for a color preview block
- A Reset button that restores all sliders to defaults

## Run

```bash
cargo run
```

## Key Code

```rust
ui.label("Brightness:");
ui.add(egui::Slider::new(&mut self.brightness, -100.0..=100.0).suffix(" %"));

ui.label("Contrast:");
ui.add(egui::Slider::new(&mut self.contrast, 0.0..=200.0).suffix(" %"));

// Preview color accounts for brightness, contrast, and saturation
let color = self.preview_color();
let (rect, _) = ui.allocate_exact_size(egui::vec2(400.0, 300.0), egui::Sense::hover());
ui.painter().rect_filled(rect, 0.0, color);
```

## Series

This is part of the [Learn egui in Neovim](https://www.youtube.com/@CelesteAI) series, where we build Rust GUI apps step by step.
