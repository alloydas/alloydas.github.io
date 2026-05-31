# alloydas.github.io

Personal academic website of **Alloy Das** — PhD student in Mechanical Engineering (Computer Vision / AI) at Iowa State University, advised by Prof. Soumik Sarkar.

🔗 **Live:** https://alloydas.github.io

## About

My research is at the intersection of **computer vision**, **multi-modal representation learning**, and **agricultural AI**. This site collects my publications, research projects (with results, figures, and interactive charts), CV, and blog.

## Built with

[Jekyll](https://jekyllrb.com/) + the [al-folio](https://github.com/alshedivat/al-folio) theme, deployed on GitHub Pages. Publications are auto-generated from [OpenAlex](https://openalex.org) by `scripts/fetch_publications.py`.

### Local development

```bash
docker compose pull && docker compose up
# open http://localhost:8080
```

Before committing, format with Prettier:

```bash
npx prettier . --write
```

## License

The underlying [al-folio](https://github.com/alshedivat/al-folio) theme is released under the [MIT License](LICENSE). Site content (text, figures, publications) © Alloy Das.
