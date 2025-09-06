# Business Intelligence Web Scraper

A comprehensive Python-based web scraping tool that aggregates business information from multiple online sources to generate detailed intelligence reports about domain names and companies.

## Overview

This script systematically collects business data from various web platforms to create comprehensive reports about companies and their online presence. It's designed for competitive intelligence, lead generation, and market research purposes.

## Features

- **Multi-Source Data Collection**: Scrapes 8+ different platforms simultaneously
- **Concurrent Processing**: Uses threading for efficient data gathering
- **Proxy Rotation**: Implements proxy management to avoid rate limiting
- **Anti-Detection**: Employs various techniques to bypass bot detection
- **Caching System**: Stores results to avoid redundant API calls
- **CSV Export**: Generates timestamped reports in CSV format

## Data Sources

| Platform | Information Collected |
|----------|----------------------|
| **EasyCounter** | Website analytics, traffic data, metadata |
| **SiteIndices** | Site valuations, daily visitor estimates |
| **Owler** | Company details, headquarters location |
| **YellowPages** | Business listings, categories, contact info |
| **CouponBirds** | Discount availability, customer ratings |
| **TrustPilot** | Customer reviews, ratings, company descriptions |
| **SimilarWeb** | Traffic rankings, visitor statistics |
| **Yelp** | Local business reviews (via Google Search API) |

## Installation

### Prerequisites

```bash
pip install requests beautifulsoup4 pandas selenium playwright
pip install cloudscraper httpx fake-useragent country-converter
pip install geopy nltk tldextract
```

### Additional Setup

1. Install Playwright browsers:
```bash
playwright install
```

2. Configure API keys in `config.py`:
   - Serper API key
   - ZenRows proxy credentials
   - Keywords Everywhere API key

3. Set up proxy list in the specified file format

## Usage

### Basic Usage

```python
# Add your domain list to utils.get_terms()
domains = ["example.com", "company.org", "business.net"]

# Run the scraper
python main_script.py
```

### Configuration

Key settings in `config.py`:

```python
# Enable/disable specific scrapers
easyCounter = True
owler = True
siteIndices = True
yellowPages = True
couponBirds = True
trustPilot = True
similarWeb = True

# Request delays (seconds)
delay_range = [1, 3]

# Service count thresholds
services_count_for_yelp = 2
services_count_for_similarWeb = 3
```

## Output

The script generates timestamged CSV reports containing:

- **Domain Information**: Company names, descriptions, categories
- **Geographic Data**: Country locations, regional rankings
- **Traffic Metrics**: Visitor counts, global/country rankings
- **Social Proof**: Reviews, ratings, social media presence
- **Business Intelligence**: Service availability, market presence

### Sample Output Columns

```
domain, EC, SI, YP, yelp, title, desc, country, category, notes
```

## Technical Details

### Architecture

- **Concurrent Execution**: Uses ThreadPoolExecutor for parallel processing
- **Error Handling**: Comprehensive exception management
- **Rate Limiting**: Implements delays and proxy rotation
- **Data Persistence**: Caches results in JSON format

### Anti-Detection Features

- Random user agent rotation
- Proxy server rotation
- Request timing randomization
- Multiple HTTP client libraries
- Headless browser support

## Legal and Ethical Considerations

### Important Disclaimers

- **Terms of Service**: This tool may violate ToS of target websites
- **Rate Limiting**: Respect website resources and implement appropriate delays
- **Data Privacy**: Ensure compliance with applicable data protection laws
- **Commercial Use**: Consider the ethical implications of automated data collection

### Recommended Usage

- Use for legitimate research purposes only
- Implement reasonable request rates
- Respect robots.txt files
- Consider reaching out to sites directly for bulk data needs

## Dependencies

```
requests>=2.25.0
beautifulsoup4>=4.9.0
pandas>=1.3.0
selenium>=4.0.0
playwright>=1.20.0
cloudscraper>=1.2.0
fake-useragent>=0.1.11
country-converter>=0.7.0
geopy>=2.2.0
nltk>=3.6
```

## Configuration Files Required

- `config.py`: API keys and scraper settings
- `utils.py`: Utility functions and data sources
- Proxy list file
- Keywords file
- Stop words file

## Troubleshooting

### Common Issues

1. **Proxy Connection Errors**: Verify proxy credentials and connectivity
2. **Rate Limiting**: Increase delay ranges in configuration
3. **API Key Errors**: Ensure all required API keys are configured
4. **Browser Crashes**: Install/update browser drivers for Selenium

### Performance Optimization

- Adjust thread pool size based on system resources
- Use high-quality proxy services
- Implement result caching to avoid redundant requests
- Monitor memory usage with large domain lists

## Contributing

This tool is intended for educational and research purposes. When contributing:

- Follow ethical scraping practices
- Implement proper error handling
- Document any new data sources
- Test thoroughly before submitting changes

## License

This project is provided as-is for educational purposes. Users are responsible for ensuring compliance with all applicable laws and terms of service.

---

**⚠️ Warning**: Web scraping at scale may violate website terms of service and could result in IP blocking or legal action. Use responsibly and consider the ethical implications of automated data collection.
