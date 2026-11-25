# Consumer Reviews Insight: Swiss Beauty Full Coverage Liquid Concealer

An independent study of 716 low-rated (1 to 3 star) Nykaa reviews, to find out what makes buyers unhappy and what the brand could fix.

**Live site:** _link added after deployment_

> Independent analysis. Not made by or affiliated with Swiss Beauty or Nykaa.

## What I found

| Problem family | Reviews (of 716) | Share |
| --- | --- | --- |
| Shade fit | 190 | 26.5% |
| How it wears (cakey, creasing, blending, oxidation, texture, lasting) | 119 | 16.6% |
| Coverage short of the "Full Coverage" claim | 116 | 16.2% |
| Quality (packaging, skin reaction) | 39 | 5.4% |
| Value | 13 | 1.8% |

- Shade fit is the largest problem. Once each tag's accuracy is accounted for, shade and wear are roughly level (about 24% and 23%).
- Price is rarely the issue: 13 complaints against 57 reviews that praise the price.
- Coverage is criticised in 116 reviews but praised in 90, which suggests part of the problem is how the product is applied.

Shares are of 1 to 3 star reviews, not of all buyers. One review can mention more than one problem.

## What the brand could do

1. **Fix the Nykaa listing** (low effort): shades in light-to-dark order, real-skin swatches, a three-question shade finder, and application tips.
2. **Run an education campaign** (medium effort): problem-first reels in buyers' own words, makeup academy partnerships, and tagged academy reels.
3. **Test the formula** (high effort): lab-test the oxidation and cakiness reports before any reformulation.

Each fix has a target to track in new reviews over two quarters.

## How it was done

1. **Collection:** Python (Playwright) collected 716 reviews rated 1 to 3 stars, with rating, shade, title, text and date. Duplicates were removed.
2. **Phrase discovery:** scikit-learn's `CountVectorizer` counted repeated two- and three-word phrases, to see what buyers actually write.
3. **Themes:** the phrases were grouped into 13 complaint themes and 5 strengths, rolled up into 5 problem families.
4. **Tagging:** keyword rules (regular expressions) tag each review, with negation handling, so "not good coverage" is a complaint and "good coverage" is praise.
5. **Clustering:** TF-IDF and K-means (K = 8) grouped the reviews to find wording the rules missed. Untagged reviews fell from 336 to 252, mostly praise-only 3-star reviews.
6. **Accuracy check:** the tags were compared with 100 reviews labelled by hand.

| Problem family | In sample | Precision | Recall | F1 |
| --- | --- | --- | --- | --- |
| Shade fit | 18 | 65% | 72% | 68% |
| Coverage | 15 | 73% | 73% | 73% |
| How it wears | 18 | 92% | 67% | 78% |

## Tools

Python, pandas, scikit-learn (CountVectorizer, TfidfVectorizer, KMeans), regular expressions, Playwright. The website is a single HTML file with no build step.

## Limitations

- Only 1 to 3 star reviews were analysed, so shares describe unhappy and mixed reviewers, not all buyers.
- The accuracy sample is small (100 reviews, one labeller), so treat scores as roughly ±10 points.
- Keyword rules miss unusual wording and Hinglish.
- Nykaa listed 895 reviews rated 1 to 3 stars; 716 were collected.

The raw review data is not included in this repository.

## Repository

- `index.html`: the website

## Author

**Sakshi Sharma**, MBA (IIM Kashipur). Interested in consumer insights and strategy roles.
shsakshi007@gmail.com
