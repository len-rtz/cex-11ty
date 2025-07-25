# Sports Club Website - 11ty Implementation

## Developer Experience (DevX) Coding Experiment

This repository contains the **11ty implementation** of a sports club website, part of a coding experiment designed to evaluate **developer experience (DevX)** when building ontology-driven websites using different static site generators.

The experiment compares **Hugo** vs **11ty** across setup, workflow, community support, cognitive load, and overall usability through structured developer diaries and NASA-TLX surveys. For more info see [cex-static-html](https://github.com/len-rtz/cex-static-html)

**Course Context:** Coding Excellence (CEX) - TH Köln, Summer Semester 2025  
**Project Website:** [archi-lab.io](https://archi-lab.io)

## How to

### Prerequisites
- Node.js (v16 or higher)
- npm

### Installation
```bash
# Clone the repository
git clone https://github.com/len-rtz/cex-static-html.git
cd cex-static-html

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

### Available Scripts
- `npm run dev` - Start development server with live reload
- `npm run build` - Build static site for production
- `npm run serve` - Serve production build locally

## Project Structure

```
├── 11ty/                   # Project root
├── _site/                  # Built files 
├── node_modules/           # Dependencies
├── src/                    # Source files
├── .eleventy.js           # 11ty config
├── package.json           # Dependencies & scripts
├── package-lock.json      # Lock file
```

## Ontology Implementation

The website implements a sports club ontology with the following entities:

### Core Entities
- **SportsClub** - Main club information and branding
- **Team** - Individual sports teams with members and schedules
- **Member** - Club members, athletes, and coaching staff
- **TrainingSession** - Regular training schedules and details
- **Tournament** - Competitions and events
- **NewsItem** - Club announcements and updates
- **MembershipApplication** - New member registration

## 11ty Configuration

### Key Features
- **Template Engine:** Nunjucks (`.njk`)
- **Content:** Markdown with front matter
- **Data:** JSON files in `_data/` directory
- **Styling:** Pico.css
- **Collections:** Auto-generated from tags and data

### Build Output
```bash
npm run build
# Generates static files in _site/ directory
```

### Development Notes
Adding New Content

- **News Posts**: Create .md files in src/news/ with tags: news
- **Team Members**: Add entries to src/_data/members.json
- **Teams**: Add entries to src/_data/teams.json
- **Training**: Add entries to src/_data/training.json

### Template Development

- **Base layout**: src/_includes/base.njk
- **Page templates**: .md files with Nunjucks templating
- **Dynamic pages**: .njk templates with pagination

### Data Relationships

- Teams reference members by ID
- Members can belong to multiple teams
- Training sessions link to specific teams
- Tournaments include participating teams
