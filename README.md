# HomePage
## A quick to use homepage application to manage your links

A self-contained, quick to use personal homepage application featuring a modern card-based interface for organizing your favorite links and services. Built with the OpenWebUI design aesthetic and includes Docker container status monitoring via Portainer integration.

It was designed to help with self hosted labs where you have too many links into containers to keep track of, and you need an easy way to manage the links. it was built using AI and is probably best updated using AI as having it all in one file inevitably makes it difficult to work with.

It can just be loaded from the github URL if you are online, or as a local file if necessary.  If loaded from github, you can also install it as a PWA (see instructions below) to have an 'app like' experience.

⚠️ **It is not designed for use with sensitive data** - the security is cosmetic and is only keeping cleartext passwords out of local files.


## 🌟 Features

### Core Functionality
- **Card-Based Link Management**: Organize your favorite websites in beautiful, responsive cards
- **Section Organization**: Create custom sections with icons and colors (Admin, AI Tools, Development, Lab, etc.)
- **Favorites System**: Quick access to your most important links
- **Search Functionality**: Fast, real-time search across all your links
- **Sitemap View**: Complete overview of all links in a multi-column layout

### Advanced Features
- **Docker Container Status**: Real-time monitoring of Docker containers via Portainer API
- **Password Management**: Encrypted storage of credentials with show/hide functionality
- **Import/Export**: Backup and restore your data with JSON export/import
- **PWA Support**: Install as a Progressive Web App for desktop and mobile
- **Theme Support**: Light/dark mode with system preference detection
- **Responsive Design**: Optimized for desktop (1080p to 4K) and mobile devices

### Security & Storage
- **Local Storage**: All data stored locally in your browser
- **Basic Encryption**: Passwords encrypted with configurable passphrase
- **Data Integrity**: Automatic backup system prevents data loss
- **No External Dependencies**: Single-file application with no remote dependencies

## 🚀 Quick Start

### Basic Setup

1. **Download**: Clone this repository or download `homepage.html`
   ```bash
   git clone [YOUR_GITHUB_REPO_URL]
   ```

2. **Open**: Simply open `homepage.html` in your web browser
   - **Local File**: `file:///path/to/homepage.html`
   - **Web Server**: Host on any HTTP/HTTPS server

3. **Configure**: Edit the configuration section at the top of the file (see [Configuration](#configuration))

### PWA Installation

To use as a Progressive Web App:

1. Add `?PWA=true` to the URL: `homepage.html?PWA=true`
2. Your browser will show an "Install App" button
3. Click to install and use as a native app

## ⚙️ Configuration

Edit the `CONFIG` object at the top of `homepage.html`:

```javascript
const CONFIG = {
    // Application Identity
    APP_ID: 'homepage-app-f7e8d9c2-a1b3-4c5d-e6f7-8g9h0i1j2k3l', // Change this for multiple instances
    SITE_INFO: {
        title: 'Personal Homepage',
        version: '1.0.0',
        author: 'Your Name Here', // TODO: Update with your information
        copyright: '2025',
        github: 'https://github.com/yourusername/your-repo' // TODO: Update with your repo URL
    },
    
    // Portainer Integration (Optional)
    PORTAINER: {
        hostname: 'localhost',     // Your Portainer hostname
        port: 9000,               // Portainer port
        apiKey: 'ptr_your-api-key-here', // TODO: Add your Portainer API key
        endpoint: 1,              // Portainer endpoint ID
        pollingFrequency: 30000   // Status check interval (30 seconds)
    },
    
    // Security Settings
    ENCRYPTION: {
        passphrase: 'whisper-mountain-keyboard' // TODO: Change this passphrase
    }
};
```

### Portainer Integration Setup

1. **Generate API Key**: 
   - Go to Portainer → User Settings → Access tokens
   - Create a new access token
   - Copy the token to `CONFIG.PORTAINER.apiKey`

2. **Configure Connection**:
   - Update `hostname` and `port` to match your Portainer instance
   - Set correct `endpoint` ID (usually 1 for local Docker)

3. **Container Monitoring**:
   - Add container IDs to your links in the app
   - Status indicators will show online/offline state

## 📱 Usage Guide

### Navigation
- **Favorites**: Default page showing starred links
- **Sections**: Custom categories in the left sidebar
- **Sitemap**: Complete overview of all links

### Managing Links
1. **Add Links**: Click "Edit" → "Add Link" → Fill form → Save
2. **Edit Links**: Enter edit mode → Click on any card → Modify → Save
3. **Organize**: Drag cards between sections or use the section dropdown
4. **Favorites**: Use the star button or checkbox to mark favorites

### Managing Sections
1. **Add Section**: Click edit icon next to "SECTIONS" → "Add Section"
2. **Delete Section**: In edit mode, click × next to section name
3. **Customize**: Set custom icons (emojis) and colors for each section

### Search & Navigation
- Use `/` to quickly focus the search box
- Search across names, URLs, and usernames
- Click any card to open the link in a new tab

### Keyboard Shortcuts
- `/` - Focus search
- `Ctrl/Cmd + E` - Toggle edit mode
- `Ctrl/Cmd + N` - Add new link (in edit mode)
- `Ctrl/Cmd + T` - Toggle theme
- `Escape` - Close modals

## 🛠️ Development & Debugging

### Debug Mode
Open browser DevTools (F12) to see:
- Portainer API responses and errors
- Performance metrics
- Analytics events
- Data storage operations

### Common Issues

**Portainer Not Working?**
- Check API key is valid and has sufficient permissions
- Verify hostname/port configuration
- Check browser console for CORS errors
- Ensure Portainer is accessible from your browser

**Data Loss Prevention**
- Application creates automatic backups every 5 minutes
- Export your data regularly via Settings → Export Data
- Data is namespaced by APP_ID to prevent conflicts

**Performance Monitoring**
- Page load times logged to console
- Container status polling performance tracked
- Search operation timing measured

### Multi-Instance Setup
To run multiple instances:
1. Change the `APP_ID` in CONFIG
2. Optionally add `siteID` URL parameter: `homepage.html?siteID=work`
3. Each instance will have separate data storage

## 🏗️ Architecture

### AI-Friendly Design
This application was designed to be maintained and modified by AI systems:
- Comprehensive documentation and comments
- Modular, readable code structure
- Consistent coding standards
- Explicit error handling
- Single-file architecture for easy modification

### Technical Stack
- **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Storage**: Browser localStorage with encryption
- **API Integration**: Portainer REST API
- **PWA**: Service Worker, Web App Manifest
- **No Dependencies**: Complete self-contained application

### File Structure
```
homepage.html
├── Configuration (CONFIG object)
├── HTML Structure
├── CSS Styles (OpenWebUI design system)
├── JavaScript Application Logic
│   ├── AppState class (main application state)
│   ├── UI rendering functions
│   ├── API integration
│   ├── PWA functionality
│   └── Analytics & error handling
└── Embedded assets and utilities
```

## 🔒 Security Considerations

- **Passwords**: Basic XOR encryption with configurable passphrase
- **API Keys**: Stored in configuration - use environment variables in production
- **CORS**: May require Portainer CORS configuration for cross-origin requests
- **Local Storage**: Data stored locally - consider browser security settings

**⚠️ Security Notice**: This application uses basic encryption for convenience. For production use with sensitive data, consider additional security measures.

## 📄 License

This is released under the GPL license - see info set in the repo

## 🤝 Contributing

Contributions are welcome! This project is designed to be AI-friendly:

1. Fork the repository
2. Make your changes to `homepage.html`
3. Test thoroughly across different browsers
4. Submit a pull request with clear description
5. Ensure code follows the existing documentation standards

### Development Guidelines
- Maintain comprehensive comments and documentation
- Follow existing code style and structure
- Test PWA functionality
- Verify Portainer integration works
- Ensure responsive design principles

## 🐛 Issues & Support

- **Bug Reports**: Use GitHub Issues with detailed reproduction steps
- **Feature Requests**: Open an issue with clear use case description
- **Questions**: Check existing issues or open a new discussion



---

**Made with ❤️ for the self-hosted community**

