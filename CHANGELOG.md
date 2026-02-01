# Changelog - TimeToFly

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/) and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.1.1] - 2026-02-01

### 🐛 Critical Fixes

#### Server Thread Blocking Fix
- **CRITICAL:** Fixed server blocking when players connect
- `FlightListener.onPlayerJoin` is now fully asynchronous
- Database operations no longer block the main thread
- New `getCachedPlayerData()` method for quick non-blocking checks
- `getPlayerDataAsync()` now returns immediately if data is cached
- Prevents connection timeouts with SQLite (pool size = 1)

### ✨ New Features

#### Colored Console Logging System
- New console logging system with ANSI colors
- Stylized startup banner with plugin version
- Logs categorized by component (DB, CACHE, PLAYER, MENU, etc.)
- Visual symbols for success (✓), error (✗), and warnings (⚠)
- Improved debug mode with detailed and colored information
- Consistent formatting for better readability

#### New Classes
- `ConsoleColors.java` - ANSI color constants
- `PluginLogger.java` - Enhanced logger with pretty formatting

### 🔧 Improvements
- Components displayed individually when loading
- Better log organization by sections
- Clearer status information for optional integrations
- FlightListener completely rewritten to be non-blocking

---

## [1.1.0] - 2026-02-01

### ✨ New Features

#### MySQL/MariaDB Support
- New support for MySQL and MariaDB databases
- Ideal for server networks (BungeeCord/Velocity)
- Simple configuration in `config.yml` with selectable database type
- Connection pooling with HikariCP for better performance
- Full compatibility with existing SQLite databases

#### In-Memory Cache System
- Implemented cache with Caffeine to reduce database queries
- Configurable automatic expiration (default 10 minutes)
- Configurable maximum cache size (default 1000 players)
- Significant latency reduction for frequent operations
- Pre-loading of data when players join
- Cache invalidation methods available

#### Soft Landing
- New fall damage protection when flight time runs out
- Automatic Slow Falling effect when time depletes
- Configurable landing period duration (default 5 seconds)
- Experimental Elytra-style gliding option
- Customizable fall speed
- Automatic fall damage cancellation during landing
- Customizable messages for start, complete, and timeout

#### Async Database Operations
- All write operations are now asynchronous
- Significant server performance improvement
- No main thread lag from database access
- `CompletableFuture` methods available for developers
- Automatic cache flush when server closes

#### Optional Messages
- Empty messages (`""`) are no longer sent
- Allows disabling redundant messages as preferred
- New `sendMessage()` methods with boolean return
- `isMessageEmpty()` method to check messages
- Documented in `messages.yml` with examples

#### Update Checker
- Automatic check for new versions on server start
- Admin notification when joining the server
- Clickable download link in chat
- Configurable in `config.yml`
- Permission: `timetofly.admin.updates`

#### Automatic Config Updater
- Configuration files are automatically updated when installing new versions
- Preserves all user-customized values
- Adds new options without losing existing configuration
- Creates automatic backups before updating (`plugins/TimeToFly/backups/`)
- Internal versioning system (`config-version`)

### 🔧 New Configuration

```yaml
database:
  type: sqlite  # or "mysql" / "mariadb"
  mysql:
    host: localhost
    port: 3306
    database: timetofly
    username: root
    password: ""
    use-ssl: false
  pool-size: 10
  cache:
    expire-minutes: 10
    max-size: 1000

flight:
  soft-landing:
    enabled: true
    duration-ticks: 100
    use-slow-falling: true
    use-elytra-glide: false
    fall-speed: 0.3
```

### 📝 New Messages
```yaml
fly:
  soft-landing-start: "⚠ Flight time depleted! Landing safely..."
  soft-landing-complete: "✓ You have landed safely."
  soft-landing-timeout: "Soft landing has ended."
```

### 📦 Added Dependencies
- HikariCP 5.1.0 (Connection pooling)
- MySQL Connector/J 8.2.0
- Caffeine 3.1.8 (In-memory cache)

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
