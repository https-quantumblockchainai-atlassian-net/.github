# 🤖 OMNI-333 Agent Quickstart

**Fast-Track Setup for Autonomous AI Agents** | 5-Minute Installation  
**Version:** 1.0.0  
**Organization:** https-quantumblockchainai-atlassian-net

---

## ⚡ 30-Second Quick Start

```bash
# 1. Clone
git clone https://github.com/https-quantumblockchainai-atlassian-net/AgentGPT.git
cd AgentGPT

# 2. Install
npm install

# 3. Configure
echo "OPENAI_API_KEY=sk_test_your_key_here" > .env.local
echo "NEXTAUTH_SECRET=$(openssl rand -base64 32)" >> .env.local
echo "NEXTAUTH_URL=http://localhost:3000" >> .env.local

# 4. Run
npm run dev

# 5. Access
open http://localhost:3000
```

---

## 🎯 What is AgentGPT?

**AgentGPT** allows you to:
- 🔧 Configure autonomous AI agents
- 🎨 Name your custom AI agent
- 🚀 Define any goal imaginable
- 🧠 Let the agent think, execute, and learn

The agent will:
1. **Think** - Break down goals into tasks
2. **Execute** - Perform actions using tools
3. **Learn** - Adjust based on results

---

## 📋 Prerequisites

```bash
# Check Node.js version
node --version  # Should be >= 16.0.0 (18+ recommended)
npm --version   # Should be >= 8.0.0

# Check Git
git --version

# Verify OpenAI API access (get key from https://platform.openai.com)
# You'll need an OpenAI API key
```

### System Requirements

| Component | Requirement |
|-----------|-------------|
| **Node.js** | >= 16.0.0 (18+ LTS recommended) |
| **NPM** | >= 8.0.0 |
| **RAM** | >= 4GB |
| **Disk Space** | >= 500MB |
| **Internet** | Required (API calls) |

---

## 🚀 Installation (3 Steps)

### Step 1: Clone & Install

```bash
# Clone the repository
git clone https://github.com/https-quantumblockchainai-atlassian-net/AgentGPT.git
cd AgentGPT

# Install dependencies
npm install
# This will take 2-3 minutes on first install

# Alternative with faster package manager
pnpm install  # or yarn install
```

### Step 2: Configure Environment

```bash
# Copy environment template
cp .env.example .env.local

# Edit .env.local with your keys
nano .env.local
# or
open .env.local
# or
code .env.local
```

**Required Variables:**

```env
# API Configuration
OPENAI_API_KEY=sk_test_your_actual_key_here

# NextAuth Configuration  
NEXTAUTH_SECRET=your_secret_key_here
# Generate: openssl rand -base64 32

NEXTAUTH_URL=http://localhost:3000

# Database (SQLite for local development)
DATABASE_URL=file:./db.sqlite
```

### Step 3: Setup & Run

```bash
# Setup database
npx prisma db push

# Start development server
npm run dev

# Server starts on http://localhost:3000
```

---

## 🔑 Getting API Keys

### OpenAI API Key (Required)

1. Go to [OpenAI Platform](https://platform.openai.com)
2. Sign up or log in
3. Navigate to **API keys** → **Create new secret key**
4. Copy the key to your `.env.local`

```bash
# Verify your key works
curl https://api.openai.com/v1/models \
  -H "Authorization: Bearer $OPENAI_API_KEY"
```

### NextAuth Secret (Auto-generate)

```bash
# Generate a random secret
openssl rand -base64 32

# Or use Node.js
node -e "console.log(require('crypto').randomBytes(32).toString('base64'))"
```

---

## 💻 Development Server

### Start Development Mode

```bash
npm run dev
```

**Output:**
```
> next dev

> AgentGPT dev server running on http://localhost:3000
```

### Access the Application

```bash
# Open in browser
open http://localhost:3000
# or
xdg-open http://localhost:3000
# or
start http://localhost:3000
```

### Hot Reload

Changes to code automatically reload the browser. No need to restart!

---

## 🎮 Using AgentGPT

### Create Your First Agent

1. **Navigate** to http://localhost:3000
2. **Name** your agent (e.g., "DataAnalyzer", "CodeBot", "ContentCreator")
3. **Set Goal** - Be specific! Examples:
   - "Analyze the sentiment of customer reviews"
   - "Generate a marketing plan for my SaaS"
   - "Create a weekly meal plan for 4 people"
4. **Click Deploy** - Watch your agent work!

### Agent Capabilities

The agent can:
- ✅ Research information
- ✅ Break down complex tasks
- ✅ Execute multiple steps
- ✅ Learn from results
- ✅ Provide detailed reporting

### Example Goals

```
"Create a comprehensive guide on machine learning for beginners"

"Analyze competitor pricing and suggest our optimal price point"

"Generate SEO recommendations for my blog"

"Create a project timeline for developing a mobile app"

"Write and optimize a LinkedIn profile summary"
```

---

## 🛠️ Available Commands

```bash
# Development
npm run dev              # Start dev server (http://localhost:3000)

# Production
npm run build            # Build for production
npm run start            # Start production server

# Testing & Quality
npm run test             # Run tests (if configured)
npm run lint             # Check code quality
npm run type-check       # Run TypeScript checks

# Database
npx prisma studio       # Open Prisma Studio (database GUI)
npx prisma db push      # Sync database schema

# Utilities
npm run clean            # Clean build artifacts
npm run format           # Format code with Prettier
```

---

## 🐳 Docker Setup (Optional)

### Quick Docker Start

```bash
# Build image
docker build -t agentgpt .

# Run container
docker run -p 3000:3000 \
  -e OPENAI_API_KEY=sk_test_your_key \
  -e NEXTAUTH_SECRET=your_secret \
  agentgpt
```

### Docker Compose

```yaml
version: '3.8'

services:
  agentgpt:
    build: .
    ports:
      - "3000:3000"
    environment:
      OPENAI_API_KEY: ${OPENAI_API_KEY}
      NEXTAUTH_SECRET: ${NEXTAUTH_SECRET}
      NEXTAUTH_URL: http://localhost:3000
      DATABASE_URL: file:./db.sqlite
    volumes:
      - ./db:/app/db
```

```bash
# Run with Docker Compose
docker-compose up
```

---

## 🔧 Troubleshooting

### Issue: "OPENAI_API_KEY is not defined"

```bash
# Check .env.local
cat .env.local

# Verify file exists
ls -la .env.local

# Re-create if needed
cp .env.example .env.local
nano .env.local
```

### Issue: "Port 3000 already in use"

```bash
# Kill process on port 3000
lsof -ti:3000 | xargs kill -9

# Or use different port
PORT=3001 npm run dev
```

### Issue: "Module not found"

```bash
# Clean install
rm -rf node_modules package-lock.json
npm install
npm run dev
```

### Issue: "Prisma error"

```bash
# Reset database
npx prisma db push --force-reset

# Or regenerate client
npx prisma generate
```

### Issue: "npm ERR! code ERESOLVE"

```bash
# Use legacy peer dependencies flag
npm install --legacy-peer-deps
```

---

## 📚 Project Structure

```
AgentGPT/
├── src/
│   ├── pages/           # Next.js pages
│   ├── components/      # React components
│   ├── server/          # Backend API (tRPC)
│   ├── env/             # Environment validation
│   └── styles/          # TailwindCSS
├── prisma/
│   └── schema.prisma    # Database schema
├── public/              # Static assets
├── .env.local          # Your local config
├── .eslintrc.json      # Linting rules
├── tsconfig.json       # TypeScript config
└── package.json        # Dependencies
```

---

## 📖 Tech Stack Explained

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Framework** | Next.js 13 | React framework with server components |
| **Language** | TypeScript | Type-safe JavaScript |
| **Styling** | TailwindCSS | Utility-first CSS |
| **UI Library** | HeadlessUI | Unstyled accessible components |
| **Database** | Prisma + Supabase | Type-safe ORM |
| **API** | tRPC | Type-safe RPC framework |
| **Auth** | NextAuth.js | Authentication |
| **Validation** | Zod | Schema validation |

---

## 🌐 Deploying to Production

### Deploy to Vercel (Recommended)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Set environment variables in Vercel dashboard
# - OPENAI_API_KEY
# - NEXTAUTH_SECRET
# - NEXTAUTH_URL (your production URL)
# - DATABASE_URL (if using cloud database)
```

### Environment Variables for Production

```env
OPENAI_API_KEY=sk_live_your_production_key
NEXTAUTH_SECRET=your_production_secret_key
NEXTAUTH_URL=https://yourdomain.com
DATABASE_URL=postgresql://user:pass@host/db
NODE_ENV=production
```

---

## 🔒 Security Best Practices

### Local Development

```bash
# Never commit .env.local
echo ".env.local" >> .gitignore

# Use different keys for dev/prod
# DEV: Use sk_test_* keys
# PROD: Use sk_* keys (production)

# Rotate keys regularly
# Check for exposed keys: git-secrets, gitleaks
```

### Production

```bash
# Use environment variable management service
# - GitHub Secrets
# - Vercel Environment Variables
# - HashiCorp Vault
# - AWS Secrets Manager

# Enable HTTPS only
# Use Content Security Policy
# Enable CORS properly
```

---

## 📊 Monitoring & Logging

### Development Logging

```bash
# Enable debug mode
DEBUG=* npm run dev

# View server logs
tail -f .next/server.log
```

### Production Monitoring

```bash
# Monitor with Vercel Analytics
# or use service like:
# - Sentry (error tracking)
# - Datadog (monitoring)
# - LogRocket (session replay)
```

---

## 🤝 Contributing

### Fork & Submit PR

```bash
# 1. Fork repository
# 2. Create feature branch
git checkout -b feature/my-feature

# 3. Make changes and commit
git add .
git commit -m "feat: description of changes"

# 4. Push and create PR
git push origin feature/my-feature
```

---

## 📖 Learning Resources

### Official Documentation
- [Next.js Docs](https://nextjs.org/docs)
- [React Docs](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Prisma Docs](https://www.prisma.io/docs/)
- [TailwindCSS Docs](https://tailwindcss.com/docs)
- [tRPC Docs](https://trpc.io/docs)

### AgentGPT Specific
- [GitHub Repository](https://github.com/https-quantumblockchainai-atlassian-net/AgentGPT)
- [Discord Community](https://discord.gg/gcmNyAAFfV)
- [Issues & Discussions](https://github.com/reworkd/AgentGPT/issues)

---

## ⏱️ Time Estimates

| Task | Time |
|------|------|
| Install Node.js | 5-10 min |
| Clone repo | 1-2 min |
| npm install | 2-3 min |
| Environment setup | 2-3 min |
| Database setup | 1-2 min |
| Start dev server | 30 sec |
| **Total** | **15-20 min** |

---

## ✅ Verification Checklist

- [ ] Node.js 18+ installed
- [ ] Repository cloned
- [ ] Dependencies installed (`npm install`)
- [ ] `.env.local` created and filled
- [ ] OpenAI API key verified
- [ ] Database initialized (`npx prisma db push`)
- [ ] Dev server running (`npm run dev`)
- [ ] Can access http://localhost:3000
- [ ] Can create and run an agent

---

## 🆘 Getting Help

### If Something Goes Wrong

1. **Check logs** - Run `npm run dev` and read error messages
2. **Clear cache** - `rm -rf node_modules package-lock.json && npm install`
3. **Check environment** - `cat .env.local`
4. **Search issues** - [GitHub Issues](https://github.com/https-quantumblockchainai-atlassian-net/AgentGPT/issues)
5. **Ask community** - [Discord](https://discord.gg/gcmNyAAFfV)

### Debug Mode

```bash
# Enable verbose logging
DEBUG=* npm run dev

# TypeScript strict mode
npm run type-check

# Lint check
npm run lint
```

---

## 🚀 Next Steps

1. **Create an agent** - Set a goal and run it!
2. **Explore API** - Check tRPC endpoints in `/src/server/api/routers`
3. **Customize UI** - Modify components in `/src/components`
4. **Read code** - Understand the structure
5. **Deploy** - Push to production on Vercel
6. **Contribute** - Help improve AgentGPT!

---

## 📞 Support

| Channel | Link |
|---------|------|
| **GitHub Issues** | [Open Issue](https://github.com/https-quantumblockchainai-atlassian-net/AgentGPT/issues) |
| **Discord** | [Join Community](https://discord.gg/gcmNyAAFfV) |
| **Twitter** | [@asimdotshrestha](https://twitter.com/asimdotshrestha) |
| **Website** | [agentgpt.reworkd.ai](https://agentgpt.reworkd.ai) |

---

**Happy agent building! 🚀**

---

**Last Updated:** May 20, 2026  
**Version:** 1.0.0  
**Status:** ✅ Current & Maintained  
**OMNI-333 Initiative**
