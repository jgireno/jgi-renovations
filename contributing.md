# Contributing to JGI Renovations Website

Thank you for your interest in contributing to the JGI Renovations website! This document provides guidelines for contributing to this project.

## How to Contribute

### Reporting Issues
If you find bugs, have suggestions, or want to request features:

1. Check existing [Issues](https://github.com/yourusername/jgi-renovations/issues) first
2. If your issue doesn't exist, create a new one
3. Provide as much detail as possible:
   - Browser and version
   - Device type (mobile/desktop)
   - Steps to reproduce
   - Screenshots if applicable

### Making Changes

#### For JGI Team Members:
1. **Clone the repository:**
   ```bash
   git clone https://github.com/jgireno/jgi-renovations.git
   cd jgi-renovations
   ```

2. **Create a new branch:**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

3. **Make your changes:**
   - Edit `index.html` for content changes
   - Test on multiple devices/browsers
   - Ensure responsive design works

4. **Test locally:**
   ```bash
   # Simple local server
   python -m http.server 8000
   # Visit http://localhost:8000
   
   # Or use Node.js
   npx http-server . -p 8000 -o
   ```

5. **Commit your changes:**
   ```bash
   git add .
   git commit -m "Add: Description of your changes"
   ```

6. **Push and create Pull Request:**
   ```bash
   git push origin feature/your-feature-name
   ```
   Then create a Pull Request on GitHub.

#### For External Contributors:
1. **Fork the repository** on GitHub
2. **Clone your fork:**
   ```bash
   git clone https://github.com/jgireno/jgi-renovations.git
   ```
3. **Follow steps 2-6 above**
4. **Create Pull Request** from your fork to the main repository

## Content Guidelines

### Adding New Services
When adding services to the website:

```html
<div class="service-card">
    <div class="service-icon">🔧</div>
    <h3 class="service-title">Service Name</h3>
    <p>Brief description of the service, focusing on benefits to homeowners.</p>
</div>
```

### Adding Gallery Images
1. **Optimize images first:**
   - Maximum width: 1920px
   - File size: Under 500KB
   - Format: JPG for photos, PNG for graphics
   - Use descriptive filenames: `kitchen-remodel-modern-white.jpg`

2. **Add to gallery:**
   ```html
   <div class="gallery-item">
       <img src="images/gallery/your-image.jpg" 
            alt="Descriptive alt text for accessibility"
            loading="lazy">
   </div>
   ```

### Writing Blog Posts
For blog section updates:
```html
<article class="blog-card">
    <div class="blog-image">📱 Icon or Image</div>
    <div class="blog-content">
        <div class="blog-date">Month DD, YYYY</div>
        <h3 class="blog-title">Engaging Title</h3>
        <p class="blog-excerpt">Brief excerpt (2-3 lines max)</p>
        <a href="#" class="read-more">Read More →</a>
    </div>
</article>
```

## Design Guidelines

### Color Scheme
- **Primary Orange:** `#FF6600` - Use for call-to-action buttons and accents
- **Dark Blue:** `#2C3E50` - Use for headings and important text
- **Light Blue:** `#3498DB` - Use for secondary accents
- **Text Colors:** `#2C3E50` for dark text, `#7F8C8D` for light text

### Typography
- **Headings:** Use the established hierarchy (h1, h2, h3, etc.)
- **Body Text:** Keep line-height at 1.6 for readability
- **Font Sizes:** Use `clamp()` for responsive sizing

### Responsive Design
- **Mobile First:** Design for mobile, then enhance for desktop
- **Breakpoints:** 
  - Mobile: < 768px
  - Tablet: 768px - 1024px  
  - Desktop: > 1024px
- **Touch Targets:** Minimum 44px for mobile buttons

## Code Standards

### HTML
- Use semantic HTML5 elements
- Include proper `alt` attributes for images
- Maintain proper heading hierarchy
- Validate HTML with [W3C Validator](https://validator.w3.org/)

### CSS
- Use CSS Custom Properties (variables) for consistency
- Follow mobile-first responsive design
- Use modern CSS features (Grid, Flexbox)
- Comment complex CSS sections

### JavaScript
- Use modern ES6+ features
- Add error handling for interactive elements
- Keep JavaScript minimal and progressive
- Comment complex functions

## Testing Checklist

Before submitting changes, test:

### Browser Testing
- [ ] Chrome (latest)
- [ ] Firefox (latest)  
- [ ] Safari (latest)
- [ ] Edge (latest)

### Device Testing
- [ ] Mobile phones (320px - 768px)
- [ ] Tablets (768px - 1024px)
- [ ] Desktop (1024px+)
- [ ] Large screens (1920px+)

### Functionality Testing
- [ ] Navigation links work
- [ ] Contact form submits
- [ ] Smooth scrolling works
- [ ] Animations perform well
- [ ] Images load properly
- [ ] No JavaScript errors in console

### Performance Testing
- [ ] Page loads in under 3 seconds
- [ ] Images are optimized
- [ ] No render-blocking resources
- [ ] Good Lighthouse scores (90+)

### Accessibility Testing
- [ ] All images have alt text
- [ ] Proper heading hierarchy
- [ ] Good color contrast ratios
- [ ] Keyboard navigation works
- [ ] Screen reader friendly

## Pull Request Guidelines

### PR Title Format
- `Add: [Description]` - for new features
- `Fix: [Description]` - for bug fixes  
- `Update: [Description]` - for content updates
- `Improve: [Description]` - for enhancements

### PR Description Template
```markdown
## Changes Made
- Bullet point list of changes

## Testing
- [ ] Tested on mobile
- [ ] Tested on desktop
- [ ] Verified responsive design
- [ ] Checked browser compatibility

## Screenshots
(Include before/after screenshots if visual changes)

## Additional Notes
Any additional context or considerations
```

## Deployment Process

1. **Automatic Deployment:** 
   - Merging to `main` branch auto-deploys via GitHub Actions
   - Check deployment status in Actions tab

2. **Manual Deployment:**
   - Can be triggered from Actions → "Deploy Website" → "Run workflow"

3. **Verification:**
   - Site updates within 2-5 minutes
   - Check live site: `https://jgireno.github.io/jgi-renovations`

## Getting Help

- **GitHub Issues:** For bug reports and feature requests
- **Email:** jgireno5159@gmail.com for urgent matters
- **Documentation:** Check `/docs/deployment.md` for deployment help

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Recognition

Contributors will be acknowledged in:
- This README file
- Website footer (for significant contributions)
- Release notes

---

**Thank you for helping make the JGI Renovations website better!** 