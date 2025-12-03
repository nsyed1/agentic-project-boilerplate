# Agentic Project Boilerplate

A comprehensive starter kit for hands-free AI-powered development with Warp.

## What's Included

### 📖 AGENTIC-DEVELOPMENT-GUIDE.md
Complete reference guide covering:
- Getting started with agentic development
- Rules overview and types
- Key principles for effective WARP.md files
- Best practices and real-world examples
- Living documentation strategies
- When and how to update rules
- Quick reference for common tasks

### 📝 WARP-TEMPLATE.md
A starter template for your WARP.md file with all essential sections:
- Project overview
- Tech stack
- Commands
- Development guidelines
- Common patterns
- Verification requirements

## Quick Start

### For a New Project

1. **Copy the template:**
   ```bash
   cp WARP-TEMPLATE.md /path/to/your-project/WARP.md
   ```

2. **Fill in project-specific details:**
   - Update tech stack
   - Add your commands
   - Document your conventions
   - Remove sections you don't need

3. **Initialize your project in Warp:**
   ```bash
   cd /path/to/your-project
   git init  # if not already a git repo
   # Run /init in Warp
   ```

### For an Existing Project

1. **Navigate to your project:**
   ```bash
   cd /path/to/your-project
   ```

2. **Run /init in Warp** to:
   - Index your codebase
   - Generate an initial WARP.md
   - Link any existing rule files

3. **Refine the generated WARP.md** using the template and guide as references

## Usage Philosophy

### Start Minimal
Don't try to document everything upfront. Start with:
- Tech stack
- Basic commands
- Essential conventions

### Grow Organically
Add to WARP.md when you:
- Repeat instructions to the agent
- Make architectural decisions
- Notice patterns emerging
- Discover mistakes or gotchas

### Review Regularly
- **Daily**: Note repeated instructions
- **Weekly**: Quick updates
- **Sprint end**: Comprehensive review
- **Quarterly**: Major cleanup

## File Structure

```
agentic-project-boilerplate/
├── README.md                          # This file
├── AGENTIC-DEVELOPMENT-GUIDE.md      # Comprehensive guide
└── WARP-TEMPLATE.md                  # Starter WARP.md template
```

## Future Plans

This boilerplate will evolve into a tool for:
- **Creating** new WARP.md files with interactive prompts
- **Refreshing** existing WARP.md files based on codebase changes
- **Maintaining** rules across multiple projects
- **Syncing** common patterns across team projects

## Contributing

As you use this boilerplate:
1. Note what works well
2. Document missing sections
3. Refine the template
4. Share improvements

## Resources

- [Warp Documentation](https://docs.warp.dev/)
- [Warp Slack Community](https://warp.dev/slack)
- [Rules Documentation](https://docs.warp.dev/knowledge-and-collaboration/rules)

## License

This is your personal boilerplate. Use, modify, and share as you see fit.

---

*Remember: The better your WARP.md, the more hands-free your coding becomes.*
