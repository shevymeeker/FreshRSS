# Personal Governmental RSS Feed Reader Setup Guide

This guide will help you set up a personal RSS feed reader specifically configured for tracking various U.S. governmental agency feeds using FreshRSS.

## Table of Contents

1. [Overview](#overview)
2. [Quick Start](#quick-start)
3. [Installation](#installation)
4. [Importing Governmental Feeds](#importing-governmental-feeds)
5. [Configuration](#configuration)
6. [Theme](#theme)
7. [Daily Usage](#daily-usage)
8. [Feed Categories](#feed-categories)
9. [Tips & Best Practices](#tips--best-practices)

---

## Overview

**What is This?**
This setup provides a pre-configured collection of RSS feeds from U.S. federal agencies, organized by department and agency type. It allows you to stay updated on official government announcements, regulatory changes, and news from a centralized dashboard.

**What is FreshRSS?**
FreshRSS is a free, self-hosted RSS aggregator. Unlike cloud-based services, all your data stays on your system—no tracking, no ads, no subscription fees.

**Included Feed Categories:**
- Legislative (Congress, Senate, House)
- Executive Office (White House, OMB)
- Federal Register & Regulations
- Treasury & Financial Agencies (Treasury, SEC, Federal Reserve)
- Labor & Employment (DOL, OSHA, EEOC)
- Health (HHS, FDA, CDC, NIH)
- Environmental (EPA, DOE, NOAA)
- Homeland Security & Defense (DHS, TSA, CBP)
- Justice & Law Enforcement (DOJ, FBI, ATF)
- State Department & Foreign Affairs
- Department of Defense
- Commerce & Trade (Commerce, USPTO)
- Transportation (DOT, FAA, NHTSA)
- Interior & Natural Resources (Interior, USGS, NPS)
- Agriculture (USDA, FDA Food)
- Education & Training
- Housing & Urban Development
- Veterans Affairs
- General Services Administration
- Independent Agencies (FCC, FTC, NASA, SSA)
- Grants & Funding (Grants.gov, SBA)
- Compliance & Regulatory Updates

---

## Quick Start

### For Docker/Container Setup:

```bash
cd /home/user/FreshRSS
docker-compose up -d
```

Then open your browser to `http://localhost:8080`

### For Local PHP Setup:

```bash
# Navigate to the FreshRSS directory
cd /home/user/FreshRSS

# Prepare directories
php cli/prepare.php

# Run the installation (command-line setup)
php cli/do-install.php --default-user admin --default-password your-secure-password

# Start a PHP server
php -S localhost:8080 -t p/

# Open browser to http://localhost:8080
```

---

## Installation

### Step 1: Install FreshRSS

**Using Docker (Recommended):**
```bash
cd /home/user/FreshRSS
docker build -t freshrss .
docker run -d \
  -p 8080:80 \
  -v freshrss-data:/data \
  --name freshrss \
  freshrss
```

**Manual Installation:**
```bash
# Requirements: PHP 8.1+, one of: SQLite, MySQL, PostgreSQL

php cli/prepare.php
php cli/do-install.php
```

### Step 2: Access FreshRSS

Open your browser and navigate to your installation URL (e.g., `http://localhost:8080` or your domain).

### Step 3: Create Your Admin User

During initial setup, create an admin account with a strong password. This is your personal access.

---

## Importing Governmental Feeds

### Option 1: Import OPML File (Easiest)

1. Log in to FreshRSS with your admin account
2. Navigate to **Settings** → **Manage subscriptions** (or **Subscriptions** in menu)
3. Select **Import** or **Import OPML**
4. Choose the file: `governmental-feeds.opml` (included in this repository)
5. Click **Import**
6. Wait for FreshRSS to fetch and organize all feeds

**FreshRSS will automatically:**
- Create feed categories matching the OPML structure
- Subscribe to all feeds
- Begin fetching content from each agency
- Organize feeds by governmental department

### Option 2: Add Feeds Manually

If you prefer to add feeds one at a time:

1. Go to **Subscriptions** → **New subscription**
2. Copy a feed URL from the list below
3. Paste it in the "Feed URL" field
4. Assign it to an appropriate category
5. Click **Subscribe**

**Popular Individual Feeds:**
- White House: `https://www.whitehouse.gov/feed/`
- Federal Register: `https://www.federalregister.gov/rss/feed.xml`
- Congress.gov: `https://www.congress.gov/rss/House.xml`
- FDA News: `https://www.fda.gov/news-events/fda-newsroom`
- EPA News: `https://www.epa.gov/rss/epa-news.xml`
- CDC Updates: `https://www.cdc.gov/media/rss.html`
- Department of Labor: `https://www.dol.gov/newsroom/rss/`

---

## Configuration

### Recommended Settings

**For Better Feed Management:**

1. **Go to Settings** → **Configuration**

2. **Feed Update Settings:**
   - Refresh interval: 2-4 hours (balances freshness with resource usage)
   - Max parallel feeds: 5-10
   - Cache duration: 3600 seconds

3. **Content Display:**
   - Show article favicons: ✓ Enabled
   - Show emoji icons: ✓ Enabled
   - View mode: "expanded" or "list" (your preference)
   - Articles per page: 25-50

4. **Archiving:**
   - Keep unread articles for: 3 months
   - Keep archived articles for: 6-12 months
   - Minimum articles per category: 100

5. **Display Preferences:**
   - Language: English (or your preference)
   - Content width: "normal" or "large"
   - Display author: ✓ Enabled
   - Display tags: ✓ Enabled

### User Preferences

1. **Theme Selection:**
   - Navigate to **Settings** → **Appearance**
   - Select **Government Official** theme (the custom theme included with this setup)
   - This theme features:
     - Professional dark blue and white government colors
     - High contrast for accessibility
     - Clear organization for tracking multiple feeds
     - Optimized typography for readability

2. **Dark Mode:**
   - Enable if you prefer dark theme
   - Set to "Auto" to match system preferences

---

## Theme

### Government Official Theme

A custom theme specifically designed for tracking governmental RSS feeds.

**Features:**
- **Professional Appearance**: Clean, official government aesthetic
- **High Contrast**: Better readability, especially for dense regulatory text
- **Organized Layout**: Clear hierarchical structure for browsing feeds
- **Accessibility**: WCAG compliant with excellent keyboard navigation
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Dark Mode Support**: Automatic dark mode for reduced eye strain

**Color Palette:**
- Primary: Official government blue (#0a1428)
- Secondary: Bright blue (#1e40af) for accents
- Neutral: Gray tones for text and borders

**Installed Location:**
`p/themes/Government/` in the FreshRSS directory

---

## Daily Usage

### Accessing Your Feeds

1. **Log in** to FreshRSS
2. You'll see your feeds organized by category in the left sidebar
3. Click a category to see all feeds within it
4. Click a feed name to see articles from that specific feed

### Reading Articles

1. **Unread articles** appear at the top
2. Click article titles to expand and read full content
3. Use keyboard shortcuts:
   - `v` - Open in new tab
   - `f` - Mark as favorite/star
   - `m` - Mark as read/unread
   - `n` - Next unread
   - `p` - Previous unread
   - `?` - Show all shortcuts

### Managing Feeds

**Mark as Read:**
- Individual article: Click the read checkbox
- Entire category: Right-click category → "Mark all as read"
- Global: Use the checkboxes and batch actions

**Archive Articles:**
- Click the archive icon to hide read articles
- Archived articles are kept but hidden from main view

**Search:**
- Use the search bar to find specific articles
- Search by title, content, or agency name

**Filter:**
- Use saved searches to create custom filters
- Example: "regulatory changes" or "CDC announcements"

### Troubleshooting Feed Updates

If a feed isn't updating:

1. Go to that feed's settings
2. Check if it requires authentication
3. View the last error message if available
4. Try clicking "Refresh" to force an update
5. Check the feed URL in a browser to ensure it's still active

---

## Feed Categories Explained

### Legislative
- **Congress.gov**: Bills, amendments, votes
- **Senate**: Senate-specific news and legislation
- **House**: House-specific news and legislation

### Executive Office
- **White House**: Official press releases and announcements
- **OMB**: Budget, regulatory guidance, memoranda

### Regulatory & Compliance
- **Federal Register**: Official government documents, proposed rules, final rules
- **Regulations.gov**: Public comment periods for federal regulations

### Treasury & Finance
- **Treasury Department**: Financial policy, international trade
- **SEC**: Securities regulations, enforcement actions
- **Federal Reserve**: Monetary policy, banking regulations

### Health & Safety
- **HHS**: Departmental policy and news
- **FDA**: Food and drug safety approvals, recalls
- **CDC**: Disease updates, health advisories
- **NIH**: Research funding announcements

### Environmental & Energy
- **EPA**: Environmental regulations and enforcement
- **DOE**: Energy policy and research
- **NOAA**: Weather, climate, oceanic data

### Labor & Employment
- **DOL**: Labor policy, employment data
- **OSHA**: Workplace safety standards
- **EEOC**: Equal employment opportunity enforcement

### Defense & Security
- **DoD**: Military news and policy
- **DHS**: Homeland security policy
- **TSA**: Transportation security alerts

### Grants & Funding
- **Grants.gov**: Federal grant opportunities (searchable)
- **SBA**: Small business grants and resources

---

## Tips & Best Practices

### 1. **Customize Categories**
- Rearrange categories by importance
- Hide categories you don't need
- Create sub-categories for related agencies

### 2. **Use Tags/Labels**
- Tag important articles for later review
- Example tags: "URGENT", "REGULATORY_CHANGE", "ACTION_REQUIRED"
- Helps you find critical items quickly

### 3. **Set Up Saved Searches**
- Create searches for frequently monitored topics
- Example: Search for "COVID-19" across all feeds
- Example: Search for "cyber" to track security alerts

### 4. **Adjust Refresh Times**
- Frequently updated sources (Federal Register): every 2 hours
- Less frequent sources (Agencies): every 6 hours
- Testing/learning: 30-60 minutes

### 5. **Mobile Access**
- If hosting on a public server, access from your phone
- FreshRSS has mobile-responsive design
- Consider using the mobile API with compatible apps

### 6. **Regular Maintenance**
- Monthly: Review and unsubscribe from unused feeds
- Quarterly: Archive old articles
- Yearly: Review category organization

### 7. **Backup Your Data**
```bash
# Export as OPML (settings-recommended)
# Go to Settings → Subscriptions → Export OPML

# Or backup database directly
cp -r data/ data-backup-$(date +%Y%m%d)/
```

### 8. **Monitoring for Changes**
- Watch the **Federal Register** for proposed rules (30-90 day comment periods)
- Follow the **White House Press Office** for presidential directives
- Subscribe to **Congressional** feeds for new legislation

### 9. **Performance Tips**
- If you have 100+ feeds, increase refresh interval to 4-6 hours
- Reduce cache duration for more fresh content
- Limit articles kept per feed if running on resource-constrained hardware

### 10. **Export & Share**
- Export as OPML to backup or share with colleagues
- Share specific subscriptions with others (if needed)
- Consider maintaining two instances: personal + shared team version

---

## Advanced Usage

### Adding Custom Feeds

If you have agency feeds not in the default list:

1. Find the feed URL (usually ends in `/rss`, `/feed.xml`, or `/news`)
2. In FreshRSS: **New subscription** → paste URL
3. Assign to category
4. Subscribe

**Common Feed URL Patterns:**
- `https://agency.gov/rss` or `/rss.xml`
- `https://agency.gov/feed` or `/feed.xml`
- `https://agency.gov/news` with RSS feed
- Search agency website for "RSS" or "Subscribe"

### Web Scraping (Advanced)

Some government sources don't provide RSS feeds. FreshRSS supports web scraping:

1. Create new subscription
2. Paste source URL
3. In advanced options, set to **HTML XPath** or **JSON** extraction
4. Use browser dev tools to identify content locations
5. Configure XPath query to extract articles

**Example:** If agency publishes press releases as HTML:
```xpath
//article[@class="press-release"]
```

---

## Support & Resources

### Troubleshooting

**Issue**: "Feed failed to update"
- **Solution**: Check if feed URL is still valid, verify internet connection

**Issue**: "All feeds showing old content"
- **Solution**: Increase refresh frequency in settings, manually click refresh

**Issue**: Missing government agencies
- **Solution**: Search agency name + "RSS feed" to find the feed URL, add manually

### Learn More

- **FreshRSS Docs**: `/home/user/FreshRSS/README.md`
- **FreshRSS GitHub**: https://github.com/FreshRSS/FreshRSS
- **Federal Register**: https://www.federalregister.gov (RSS available on each page)
- **Congress.gov**: https://www.congress.gov (RSS feeds for bills, votes, members)

### API & Integration

FreshRSS supports:
- **Google Reader API**: Compatible with mobile RSS apps
- **Fever API**: Compatible with Reeder, Unread, and others
- **Direct API access**: For custom integrations

---

## Keeping Your Reader Current

### Monthly Tasks
- Review and remove unused feeds
- Check for new agency announcements/feeds
- Export backup of your subscriptions

### Quarterly Tasks
- Archive old articles (keep last 3 months)
- Review feed organization
- Update custom searches if needed

### Yearly Tasks
- Full backup of database
- Review all subscriptions
- Plan any major reorganization

---

## Privacy & Security

**Your Data is Yours:**
- All feed data stored locally on your system
- No tracking or analytics
- No advertising
- Not shared with third parties

**Security Best Practices:**
- Use strong passwords for admin account
- If hosting publicly, use HTTPS
- Regularly update FreshRSS to latest version
- Keep your server/system updated

---

## Example Daily Workflow

**Morning (15 minutes):**
1. Log in to FreshRSS
2. Check "Unread" count
3. Browse White House & Congress feeds
4. Star any urgent items
5. Mark department news as read

**Afternoon (10 minutes):**
1. Check Federal Register for new proposed rules
2. Review any tagged items from morning
3. Export important articles to PDF if needed

**End of Week (30 minutes):**
1. Review all starred articles
2. Export/forward important items to relevant teams
3. Archive read articles
4. Plan any feed subscription changes

---

## Questions?

For issues with:
- **FreshRSS setup**: See `/home/user/FreshRSS/README.md`
- **Feed subscriptions**: Check the feed URL directly in browser
- **FreshRSS functionality**: Visit https://github.com/FreshRSS/FreshRSS/issues
- **Government feeds**: Search agency website for RSS or news feeds

---

**Last Updated**: January 2026
**FreshRSS Version**: 1.28.1+
**Setup Version**: 1.0
