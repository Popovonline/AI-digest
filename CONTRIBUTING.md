# Contributing

Thank you for your interest in contributing to AI Digest!

## How to Contribute

### Reporting Issues

- Use GitHub Issues to report bugs or suggest features
- Check existing issues before creating a new one
- Include clear description and steps to reproduce

### Adding Sources

1. Fork the repository
2. Edit `config/sources.json`
3. Add your source with required fields:
   ```json
   {
     "id": "unique-id",
     "name": "Source Name",
     "url": "https://example.com/feed",
     "category": "category-name"
   }
   ```
4. Submit a pull request

### Source Requirements

- Must be publicly accessible (no paywall)
- Should publish AI, product, or tech content
- Should update at least weekly
- English language preferred

### Improving Scoring

1. Review `docs/SCORING.md`
2. Suggest changes via Issue or PR
3. Include rationale for threshold adjustments

### Format Changes

1. Review `docs/TEMPLATE.md`
2. Test changes with sample data
3. Submit PR with before/after examples

## Code of Conduct

See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)

## Questions?

Open an Issue with the "question" label.
