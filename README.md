# EyeSeed 🌱

> **DATT3700 Collaborative Project Development**  
> Embodied AI Flower - Physical Computing LCD Display Driver Preview

[![GitHub](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![DATT3700](https://img.shields.io/badge/course-DATT3700-orange)](https://datt3700.com)

Interactive eye animation preview tool for ESP32-driven LCD display in embodied AI flower installation.

## ✨ Features

- 🎨 **Real-time Eye Rendering** - Firmware-level accurate 1:1 rendering of animated eyes
- 🌐 **Bilingual Interface** - Switch between English and Chinese instantly
- 📁 **One-Click Loading** - Auto-detect and load eye graphics from header files
- 🎮 **Interactive Controls**
  - Adjustable gaze (X/Y offset)
  - Blink control
  - Iris/pupil scaling
  - Pupil shape (round to cat-eye)
  - Auto-animation with physics
- 🔧 **Hardware Configuration**
  - Customizable LCD resolution
  - Centered viewport option
  - Skin tone customization

## 🚀 Quick Start

### Online Demo
Visit: https://dattodigm.github.io/eyeseed/

### Local Development

1. **Clone the repository**

    ```bash 
    git clone https://github.com/yourusername/eyeseed.git 
    cd eyeseed
    ```

2. **Open with a local server** (required for fetch API)
   
   Using Python:
   ```bash
    python3 -m http.server 8000
    ```
   
    Using Node.js:
    ```bash
    npx serve .
    ```
3. **Access the application**
   Open browser to `http://localhost:8000`

## 📖 Usage Guide

### Loading Eye Graphics

1. In the **"Available Header Files"** section, click any `.h` file:
   - `catEye.h` - Feline vertical slit pupils
   - `defaultEye.h` - Standard human-like eye
   - `goatEye.h` - Rectangular pupils
   - `owlEye.h` - Large round pupils
   - `terminatorEye.h` - Red robotic glow
   - And more...

2. The code automatically loads and parses into layers

3. Adjust parameters in real-time to preview on your LCD configuration

### Layer Management

- **Drag & Drop** - Reorder layers using the ☰ handle
- **Enable/Disable** - Toggle individual layers with checkboxes
- **Render Mode** - Choose per-layer rendering:
  - `RGB565` - Standard image mapping (sclera/white of eye)
  - `POLAR` - Polar inversion mapping (iris colored part)
  - `THRESHOLD` - Threshold mask (eyelids)

### Animation Controls

| Control | Description | Range |
|---------|-------------|-------|
| **Gaze X/Y** | Eye movement offset | -50 to 50px |
| **Blink** | Eyelid openness | 0% (closed) to 100% (open) |
| **Iris Scale** | Colored part size | 0.1 to 1.5 |
| **Pupil Size** | Black center size | 0.1 to 0.9 |
| **Pupil Shape** | Round to slit | 1.0 (round) to 0.5 (cat) |
| **Animation** | Enable auto-movement | Toggle + speed control |

## 🔧 Technical Background

This project reverse-engineers the Adafruit Uncanny Eyes firmware for educational purposes, specifically designed for:

- **Hardware**: GC9D01 0.71" LCD Module (160x160)
- **Microcontroller**: ESP32
- **Course**: DATT3700 Collaborative Project Development
- **Application**: Embodied AI Flower installation

### How It Works

The JavaScript renderer replicates the embedded C++ pipeline:

```paintext
Original Firmware Flow:
┌─────────────┐    ┌──────────┐    ┌──────────┐    ┌─────────┐
│ Sclera Map  │───▶│ Iris Map │───▶│ Eyelids  │───▶│ LCD DMA │
│ (RGB565)    │    │ (POLAR)  │    │(THRESHOLD)│    │ Buffer  │
└─────────────┘    └──────────┘    └──────────┘    └─────────┘

JavaScript Replication:
┌─────────────┐    ┌──────────┐    ┌──────────┐    ┌─────────┐
│ Parse .h    │───▶│ Canvas   │───▶│ Blend    │───▶│ Screen  │
│ Files       │    │ Renderer │    │ Layers   │    │ Display │
└─────────────┘    └──────────┘    └──────────┘    └─────────┘
```

### Key Algorithms Implemented

1. **RGB565 Decoding** - 16-bit color to RGB triplet conversion
2. **Polar Coordinate Mapping** - Cartesian to polar transformation for iris rendering
3. **Eyelid Tracking** - Dynamic threshold calculation based on gaze direction
4. **Autonomous Animation** - Fractal-based eye movement simulation
5. **Physical Blink Model** - Ease-in/out curves for natural eyelid motion

## 📚 References & Credits

This project was built upon the amazing work of:

- **Adafruit Industries** - [Uncanny Eyes Library](https://github.com/adafruit/Uncanny_Eyes/)
  - Original concept and implementation by Phil Burgess / Paint Your Dragon
  - [Monster Mask Documentation](https://learn.adafruit.com/monster-mask-augmented-eyes-toon-hat/graphics)
  
- **Bodmer** - [TFT_eSPI Animated Eyes](https://github.com/Bodmer/TFT_eSPI/tree/master/examples/Generic/Animated_Eyes_1)
  - ESP32 optimization and adaptation
  
- **WaveShare** - [0.71" LCD Module Documentation](https://www.waveshare.com/wiki/0.71inch_LCD_Module)
  - Hardware specifications and pinout
  
- **Adafruit Learning System** - [Customizing Eye Graphics](https://learn.adafruit.com/adafruit-monster-m4sk-eyes/customizing)

## 🛠️ Development

### Project Structure

```paintext
eyeseed/
├── index.html          # Main application (bilingual UI)
├── data/               # Pre-converted eye graphics
│   ├── catEye.h
│   ├── defaultEye.h
│   └── ...
├── eye_functions.cpp   # Original firmware reference
└── README.md           # This file
```

### Adding Custom Eye Graphics

1. Create or convert eye graphics to C header format
2. Place `.h` files in the `data/` directory
3. Update the file list in `index.html` line 737:
```javascript
   const files = [
     'yourNewEye.h',
     // ... existing files
   ];
```
### Modifying Default Settings

Edit `index.html`:
- Line 283-291: Default LCD resolution
- Line 309: Default skin color
- Line 414: Default zoom level

## 🎓 Course Context

**DATT3700 - Collaborative Project Development**  
This tool was created to facilitate team communication and rapid prototyping for the Embodied AI Flower project. It allows team members to:

- Preview eye animations before deploying to hardware
- Experiment with different eye designs
- Understand the rendering pipeline
- Debug visual issues without reflashing the ESP32

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details

The original Adafruit Uncanny Eyes library is released under the MIT license.

## 🤝 Contributing

这是一个为了增强 DATT3700 course project 而创建的工具，旨在帮助团队成员更好地理解和预览 ESP32 LCD 显示的眼睛动画效果。欢迎任何形式的贡献，无论是改进功能、修复 bug 还是优化性能，都非常感谢！

Feel free to fork and adapt for your own projects!

## TODO

### 🚧 Roadmap / 路线图

- [ ] **Image Converter Tool** - Convert PNG/JPEG to C header format  
      **图像转换工具** - 将 PNG/JPEG 转换为 C 头文件格式

- [ ] **More Preset Eye Designs** - Expand library with custom eye styles  
      **增加更多预设眼睛设计** - 扩展自定义眼睛样式库

- [ ] **Animation Performance Optimization** - Support higher frame rates (>60 FPS)  
      **优化动画性能** - 支持更高帧率（>60 FPS）

- [ ] **Enhanced Interactive Controls** - Blink frequency, pupil shape customization  
      **添加更多交互控制** - 如眨眼频率、瞳孔形状等

- [ ] **Eye Animation Sequence Recording & Playback**  
      **眼睛动画序列录制与回放**

- [ ] **Multi-language Support Expansion** - Add Japanese, Korean, etc.  
      **多语言支持扩展** - 添加日语、韩语等

- [ ] **Mobile Responsive Design** - Touch-friendly controls for smartphones/tablets  
      **移动端响应式设计** - 适配手机/平板的触控操作

- [ ] **Real-time Collaboration Mode** - Multiple users preview simultaneously  
      **实时协作模式** - 多用户同时预览

- [ ] **Export Configuration Presets** - Save and share LCD settings  
      **导出配置预设** - 保存和分享 LCD 设置

- [ ] **WebUSB Support** - Direct firmware upload from browser  
      **WebUSB 支持** - 从浏览器直接上传固件

- [ ] **3D Preview Mode** - Simulate eye appearance on curved surfaces  
      **3D 预览模式** - 模拟曲面显示效果

- [ ] **Audio Reactive Eyes** - Synchronize animation with sound input  
      **音频反应眼睛** - 根据声音输入同步动画

- [ ] **Team Documentation** - Contribution guidelines for teammates  
      **团队文档** - 为队友添加贡献指南

- [ ] **Hardware Integration Guide** - ESP32 pinout and wiring diagrams  
      **硬件集成指南** - ESP32 引脚图和接线图

- [ ] **Performance Profiling Tools** - Frame timing and memory usage analysis  
      **性能分析工具** - 帧时间和内存使用分析

### 💡 Additional TODO Suggestions

> #### 🎨 Design & UX
> - **Custom Eye Creator** - Visual editor to design eyes without coding
> - **Color Palette Presets** - Pre-configured color schemes for different moods/themes
> - **Preview on Different Screen Shapes** - Circle, rectangle, custom masks
> 
> #### 🔧 Technical
> - **TypeScript Migration** - Better type safety and IDE support
> - **Unit Tests** - Test rendering functions and layer parsing
> - **CI/CD Pipeline** - Automated testing on pull requests
> - **Bundle Size Optimization** - Reduce initial load time
> 
> #### 🌸 Project-Specific (Embodied AI Flower)
> - **Flower Growth Animation** - Integrate eye movement with flower blooming stages
> - **Environmental Sensor Integration** - React to light, temperature, touch
> - **Multi-Flower Synchronization** - Coordinate eyes across multiple installations
> - **Day/Night Cycle Adaptation** - Auto-adjust based on ambient light
> 
> #### 👥 Team Collaboration
> - **Code Comments in Both Languages** - Ensure all teammates understand
> - **API Documentation** - For future developers
> - **Video Tutorials** - Quick start guide for non-technical team members
- **Troubleshooting Guide** - Common issues and solutions

## 📞 Contact

For questions about this project, please open an issue on GitHub.

---

<div align="center">

**Made with ❤️ for DATT3700**  
*Bringing digital eyes to botanical installations 🎨👁️🌸*

</div>

