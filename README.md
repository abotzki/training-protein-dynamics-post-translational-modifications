# Assess protein dynamics & post-translational modifications 
**Through ELIXIR Belgium Node services: B2BTools & Scop3P**

[![DOI](https://zenodo.org/badge/1120984068.svg)](https://doi.org/10.5281/zenodo.18242775)

--- 

The breakthrough of AlphaFold2 delivered structural models for nearly all proteins lacking experimental structures, opening new avenues to interrogate both sequence and structure. However, these models capture static snapshots rather than the dynamic conformational ensembles that govern protein behaviour.

The Bio2Byte Tools, published as B2BTools, is a suite of sequence-based predictors for unveiling the biophysical properties hidden in the amino acid language with ease: backbone dynamics, early folding events, disordered positions among other features. Developed by the lab led by Prof. Dr. Wim Vranken, this online platform is part of the ELIXIR Belgium node services. In parallel to this suite of tools, Scop3P, another ELIXIR Belgium node service, will allow you to explore and understand the impact of phospho-sites on human protein structure and function. It can serve as a springboard for researchers seeking to analyse and interpret a given phosphorylation site or phosphoprotein in a structural, biophysical, and biological context.

## Open this training

Please visit our (training material)(https://bio2byte.github.io/training-protein-dynamics-post-translational-modifications/). 

## Citing this lesson

Please cite as:

  1. **Pathmanaban Ramasamy**, **Adrián Díaz** (2026). Training Material: Assess protein dynamics & post-translational modifications. Zenodo. [https://doi.org/10.5281/zenodo.18242776](https://doi.org/10.5281/zenodo.18242776).

---

## Local installation

This website is generated with [MkDocs](https://www.mkdocs.org/), with the theme [Material](https://squidfunk.github.io/mkdocs-material/).

To host it locally, create an environment:

```bash
conda create --name mkdocs python==3.13
```

Then install MkDocs via `pip`:
```bash
pip install mkdocs
```

and Material with some plugins:
```bash
pip install mkdocs-material
pip install mkdocs-video
pip install mkdocs-bibtex 
pip install neoteroi-mkdocs
pip install addbioschemas
```

Clone this repository to your local computer. Then, make the repository your current directory and type:

To host it locally: 

```bash
mkdocs serve --watch ./docs --livereload
```

Live reload will update the generated output automatically every time a change is detected in the docs directory. 

Check it out with your browser at [http://localhost:8000/](http://localhost:8000/).

# About the training Template 

For instruction on how to use the template, please follow this documentation: 
https://elixir-europe-training.github.io/ELIXIR-TrP-LessonTemplateInstructions-MkDocs/


**Any issues?** Contact Geert van Geest (@GeertvanGeest) 


## Citation

Please cite as

> Geert van Geest, Elin Kronander, Jose Alejandro Romero Herrera, Nadja Žlender, & Alexia Cardona. (2023). 
> The ELIXIR Training Lesson Template - Developing Training Together (v1.0.0-alpha). Zenodo. 
> https://doi.org/10.5281/zenodo.7913092
