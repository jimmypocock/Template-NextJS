# Next.js AWS Template

A production-ready Next.js template with comprehensive AWS infrastructure, Google Analytics, Google AdSense, and modern web development tools.

## Features

### 🚀 Modern Tech Stack
- **Next.js 15** with App Router
- **TypeScript** for type safety
- **Tailwind CSS** for rapid UI development
- **ESLint** for code quality

### 🔧 Google Integrations
- **Google Analytics** with consent management
- **Google AdSense** with privacy-compliant setup
- **Cookie Consent Management Platform (CMP)**

### ☁️ AWS Infrastructure
- **Complete CDK setup** with multiple stacks
- **CloudFront CDN** for global content delivery
- **S3** for static hosting
- **Certificate Manager** for SSL
- **WAF** for security
- **Lambda@Edge** for edge functions
- **CloudWatch** monitoring and alerts

### 🎨 UI/UX Features
- **Dark/Light theme** toggle
- **Responsive design** for all devices
- **Beautiful gradient backgrounds** with animated orbs
- **Glass morphism** design elements
- **Accessible** and SEO optimized

## Quick Start

### 1. Clone and Setup

```bash
# Clone this template
git clone <your-template-repo> your-project-name
cd your-project-name

# Install dependencies
npm install

# Copy environment file
cp .env.example .env
```

### 2. Configure Environment Variables

Edit `.env` with your values:

```bash
# Google Analytics
NEXT_PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX

# Google AdSense
NEXT_PUBLIC_ADSENSE_CLIENT_ID=ca-pub-XXXXXXXXXXXXXXXXX

# AWS Configuration
AWS_REGION=us-east-1
AWS_ACCOUNT_ID=123456789012
DOMAIN_NAME=yourdomain.com

# Application
APP_NAME=your-app-name
```

### 3. Start Development

```bash
# Start development server
npm run dev

# Open http://localhost:3000
```

## Customization Guide

### 🎨 Brand Colors

Update your brand colors in `app/globals.css`:

```css
:root {
  --primary: #9436eb;      /* Your primary brand color */
  --secondary: #2196f3;    /* Your secondary brand color */
  --accent: #ec4899;       /* Your accent brand color */
  --neutral: #9ca3af;      /* Your neutral brand color */
}
```

Also update `tailwind.config.ts`:

```typescript
theme: {
  extend: {
    colors: {
      primary: "#9436eb",
      secondary: "#2196f3", 
      accent: "#ec4899",
      neutral: "#9ca3af",
    },
  },
},
```

### 📝 Content Updates

#### App Metadata
Update `app/layout.tsx`:
- Title and description
- Open Graph metadata
- Schema markup
- Keywords

#### Page Content
- `app/page.tsx` - Home page
- `app/about/page.tsx` - About page
- `app/how-it-works/page.tsx` - Documentation
- `app/privacy/page.tsx` - Privacy policy
- `app/terms/page.tsx` - Terms of service

#### Package Information
Update `package.json`:
```json
{
  "name": "your-app-name",
  "description": "Your app description"
}
```

### 🔧 Google Services Setup

#### Google Analytics
1. Create a GA4 property at [analytics.google.com](https://analytics.google.com)
2. Copy your Measurement ID (G-XXXXXXXXXX)
3. Update `NEXT_PUBLIC_GA_MEASUREMENT_ID` in `.env`

#### Google AdSense
1. Apply for AdSense at [adsense.google.com](https://adsense.google.com)
2. Get your Publisher ID (ca-pub-XXXXXXXXXXXXXXXXX)
3. Update `NEXT_PUBLIC_ADSENSE_CLIENT_ID` in `.env`
4. Update `public/ads.txt` with your Publisher ID

## AWS Deployment

### Prerequisites

1. **AWS CLI** configured with appropriate credentials
2. **AWS CDK** installed globally: `npm install -g aws-cdk`
3. **Domain** registered (for production deployment)

### Installation

```bash
# Install CDK dependencies
npm run cdk:install

# Bootstrap CDK (first time only)
npx cdk bootstrap
```

### Deployment Options

#### Option 1: Deploy Everything (Recommended)
```bash
npm run deploy:all
```

#### Option 2: Deploy Individual Stacks
```bash
# Deploy in order:
npm run deploy:foundation
npm run deploy:cert
npm run deploy:edge
npm run deploy:waf
npm run deploy:cdn
npm run deploy:app
npm run deploy:monitoring
```

### Infrastructure Overview

| Stack | Purpose | Resources |
|-------|---------|-----------|
| Foundation | Core infrastructure | S3 buckets, IAM roles |
| Certificate | SSL certificates | ACM certificates |
| Edge Functions | Lambda@Edge functions | Lambda functions |
| WAF | Web security | WAF rules, IP filtering |
| CDN | Content delivery | CloudFront distribution |
| App | Application hosting | S3 static hosting |
| Monitoring | Observability | CloudWatch dashboards |

### Post-Deployment

```bash
# Check deployment status
npm run status:all

# Enable maintenance mode
npm run maintenance:on

# Disable maintenance mode
npm run maintenance:off
```

## Development Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with Turbopack |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run cdk:synth` | Synthesize CDK templates |
| `npm run status` | Check stack status |

## File Structure

```
├── app/                    # Next.js App Router pages
│   ├── globals.css        # Global styles
│   ├── layout.tsx         # Root layout
│   ├── page.tsx           # Home page
│   ├── about/             # About page
│   ├── how-it-works/      # Documentation
│   ├── privacy/           # Privacy policy
│   └── terms/             # Terms of service
├── components/            # Reusable React components
│   ├── AdSense/           # Google AdSense components
│   ├── GoogleAnalytics.tsx
│   ├── GoogleCMP.tsx      # Cookie consent
│   └── ThemeToggle.tsx
├── cdk/                   # AWS CDK infrastructure
│   ├── src/               # CDK stack definitions
│   └── package.json       # CDK dependencies
├── scripts/               # Deployment scripts
├── public/                # Static assets
└── .env.example           # Environment variables template
```

## Best Practices

### 🔒 Security
- All secrets in environment variables
- WAF protection enabled
- HTTPS enforced
- Content Security Policy headers

### 📊 Performance
- Next.js optimizations enabled
- CDN caching configured
- Image optimization
- Bundle analysis available

### ♿ Accessibility
- Semantic HTML structure
- ARIA labels where needed
- Keyboard navigation support
- Color contrast compliance

### 🔍 SEO
- Meta tags optimized
- Structured data markup
- Sitemap included
- robots.txt configured

## Monitoring & Maintenance

### CloudWatch Dashboards
Access monitoring dashboards in AWS Console:
- Application performance metrics
- Error tracking and alerts
- Infrastructure health monitoring

### Maintenance Mode
```bash
# Enable maintenance mode
npm run maintenance:on

# Disable maintenance mode
npm run maintenance:off
```

### Log Monitoring
- CloudFront access logs
- Lambda@Edge function logs
- Application error tracking

## Troubleshooting

### Common Issues

**Build Errors**
```bash
# Clear Next.js cache
rm -rf .next

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

**CDK Deployment Errors**
```bash
# Check AWS credentials
aws sts get-caller-identity

# Verify CDK bootstrap
npx cdk bootstrap

# Check stack status
npm run status:all
```

**Environment Variables**
- Ensure all required variables are set in `.env`
- Check AWS credentials and permissions
- Verify domain ownership for certificates

### Getting Help

1. Check the AWS CloudFormation console for detailed error messages
2. Review CloudWatch logs for runtime issues
3. Use `npm run diagnose:stack` for troubleshooting specific stacks

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

[Your License Here]

## Support

For support, please contact [your-email@example.com] or create an issue in the repository.

---

## Next Steps

After setting up your template:

1. **Customize branding** - Update colors, fonts, and content
2. **Configure domains** - Set up your production domain
3. **Deploy infrastructure** - Run the CDK deployment
4. **Set up monitoring** - Configure alerts and dashboards
5. **Launch your app** - Go live with confidence!

Happy building! 🚀