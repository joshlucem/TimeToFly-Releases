# Changelog - TimeToFly

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/) and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.3] - 2026-01-29

### 🐛 Fixed
- Incorrect message key for flight cooldown (`flight.cooldown-active` → `fly.cooldown-active`)
- Error "missing required data class java.lang.Float" when spawning particles
- Error "data should be class java.lang.Void" with certain particle types
- Improved particle data type handling using `particle.getDataType()`
- Automatic fallback for particles that don't require data
- Unused imports and deprecated methods in code

### ✨ Improved
- More robust and compatible particle spawning system
- Better error handling with informative messages
- Clean code without compilation warnings

## [1.0.2] - 2026-01-20

### ✨ Added
- Enhanced menu system with better pagination
- Additional particle effects
- Improved database performance

### 🐛 Fixed
- Minor UI glitches in menus
- Database connection stability

## [1.0.0] - 2024-01-10

### ✨ Added

#### Core System
- ✈️ Flight time management with customizable consumption
- 💾 SQLite database with automatic purge of inactive players
- 🌍 World control - define which worlds allow flight
- ⚙️ Fully customizable YAML configuration system

#### Player Commands
- `/fly` - Toggle flight mode
- `/fly settings` - Open flight configuration menu
- `/fly shop` - Display shop information

#### Administrator Commands
- `/flyadmin add <player> <time>` - Add flight time
- `/flyadmin remove <player> [time]` - Remove flight time
- `/flyadmin info <player>` - Display player information
- `/flyadmin reload` - Reload configuration without restart
- `/flyadmin debug on/off` - Toggle debug mode

#### Menu System
- 📋 Main settings menu (36 slots)
- ⏱️ Alert configuration menu
- 🎨 Particle effects menu with 10+ options
- ✅ Configuration persistence in database

#### Particle Effects
- 💔 Hearts
- ✨ Magic
- 🔥 Fire
- 💧 Water
- ⚡ Redstone
- 🎵 Musical Notes
- ❄️ Snow
- ☁️ Clouds
- 👻 Soul
- 🌈 Rainbow (and more)

#### Alert System
- ⏲️ Configurable time-based alerts
- 🔊 Customizable sounds per threshold
- 📢 Colour-coded alert messages
- 📊 Alert history in database

#### Message System
- 📝 MiniMessage support with 150+ message keys
- 🎨 Full colour and formatting support
- 🌐 Customisable prefixes (error, success, warning)
- 📦 Organized by category

#### PlaceholderAPI Integration
- 📊 12 dynamic placeholders for scoreboards and chat
- 🎯 Time, status, effects, alerts placeholders
- 📈 Visual progress bar
- ⚙️ Customizable through `placeholder.yml`

#### Debug Mode
- 🐛 Category-based debug system
- 📋 Complete logging of:
  - Player activities
  - Database operations
  - Command execution
  - Menu interactions
- ✅ No performance impact when disabled

#### ItemsAdder Support
- 🎭 Custom item support in menus
- 🖼️ Personalized menu appearance
- 🔧 Simple configuration in `config.yml`

#### Additional Features
- 🛡️ WorldGuard integration for region restrictions
- 🎭 Tebex compatibility for automatic shop integration
- 🔐 Granular permission system
- 📝 Fully customizable configuration files
- 🌍 Multi-language support (Spanish + more)

---

## Download

Visit the [releases](https://github.com/joshlucem/TimeToFly-Releases/releases) folder to download the latest version.

## Support

- 💬 [Discord Community](https://discord.gg/UzXWvshGfh)
- 📖 Check configuration files for detailed options
- 🐛 Report issues in the Spigot discussion section
