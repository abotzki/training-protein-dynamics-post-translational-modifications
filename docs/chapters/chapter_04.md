## 4.1 Why Scop3P as the go-to for modifications ?

Protein phosphorylation is a key post-translational modification involved in many biological processes and is strongly associated with human diseases such as cancer and metabolic disorders.

Accurate identification, annotation, and functional analysis of phosphorylation sites (phosphosites) are therefore essential to understand their biological roles. Phosphosites are mainly studied using phosphoproteomics approaches, which have produced large amounts of publicly available data. Several resources have been developed to collect and organize phosphosite information, but most of them focus primarily on protein sequences and basic site-level metadata.

Other resources often contain false positives and doesn't include the experimental metadata (localization probability, FDR, database used for searching)

<figure>
    <img src="../../assets/images/Mass spec1.png" width="600" alt="Mass-spec picture goes here"/>
    <figcaption> Mass-spec figure 1 </figcaption>
</figure>

<figure>
    <img src="../../assets/images/mass spec2.1.png" width="600" alt="Mass-spec picture goes here"/>
    <figcaption> Mass-spec figure 2 </figcaption>
</figure>

<figure>
    <img src="../../assets/images/mass spec2.2.png" width="600" alt="Mass-spec picture goes here"/>
    <figcaption> Mass-spec figure 3 </figcaption>
</figure>

What is often missing from these resources is biological and structural context, including mapping to protein structures, experimental provenance, and biophysical annotations.

<figure>
    <img src="../../assets/images/Protein coverage.png" width="600" alt="Image on elixir landing page"/>
    <figcaption> Protein coverage </figcaption>
</figure>

ScoP3P addresses this gap by integrating protein sequences (UniProtKB/Swiss-Prot), structural data (PDB), and uniformly reprocessed phosphoproteomics datasets (PRIDE) to annotate all known human phosphosites. In addition, each phosphoprotein is enriched with per-residue biophysical annotations, including structural propensity, solvent accessibility, disorder probability, and early folding regions.

ScoP3P, available at [https://iomics.ugent.be/scop3p](https://iomics.ugent.be/scop3p), provides a dedicated platform for the visualization and analysis of phosphosites and supports the study of phosphosite–structure–function relationships.


!!! question "Chapter questions"

    1. How should Scop3P information be interpreted for a given protein target?
    2. How can PTMs be linked to structural data, such as predicted models or experimental structures from the PDB?
    
---

## 4.2 Exploring experimentally supported PTMs

### 4.2.1 Via the webserver 

!!! example "Hands-on: Website usage"

    1. Explore the PTM map over the sequence length using lollypop plot.
    1. Link the lollypop information to the structural representation.
        1. Toggle between experimental and predicted structures.
        1. Change visualisation properties such as style and colour.
    1. Find the modification metadata from the summary table.
    1. Explore the biophysical circular plot.
        1. Mouse over to view the values.
    1. From the peptide table, explore the phospho-sites identified by mass spectrometry experiments (project information, species, tissue/cell type).
        1. Hint: you can also visualise the original spectra using the **USI** link.
    1. From the structures table, explore the modifications related to experimental structures.
        1. Hint: you can explore 
            * The secondary-structure information (conservation, surface accessibility)
            * Do you see multiple conformational state for the same protein ?
    1. From the mutations table, explore the natural variant and the disease context.
    
    ??? success "Solution"

        Exploring the modifications:
        
        <figure>
            <img src="../../assets/images/SCOP3P_P07949.jpg" width="1000" alt="Image on elixir landing page"/>
            <figcaption> Linking the lollypop information to the structural representation </figcaption>
        </figure>
        
        Viewing the phospho projects:
        
        <figure>
            <img src="../../assets/images/phospho_table.jpg" width="1000" alt="Image on elixir landing page"/>
            <figcaption> explore the phospho-sites identified by mass spectrometry experiments </figcaption>
        </figure>
        
        Structures and mutations:
        
        <figure>
            <img src="../../assets/images/scop3p_last_tables.jpg" width="1000" alt="Image on elixir landing page"/>
            <figcaption> Exploring the modifications related to experimental structures and diseases </figcaption>
        </figure>


### 4.2.3 Via the REST API

!!! example "Hands-on: REST API usage"
    
    For this activity open this interactive notebook: `Scop3P_API.ipynb`: 
    <a target="_blank" href="https://colab.research.google.com/github/Bio2Byte/Scop3P-notebooks/blob/main/Scop3P_API.ipynb">
        <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
    </a>
    
    1. Fetch protein sequence from UniProt
    1. Fetch modifications from Scop3P
    1. Parse the data
    1. Explore the functional scores
    
    ??? success "Solution"

        1. Open the [Colab Notebook](https://colab.research.google.com/github/Bio2Byte/Scop3P-notebooks/blob/main/Scop3P_API.ipynb).
        1. Install the dependencies
        1. Change the "Target protein" to "P07949"
        1. Fetch the canonical sequence from UniProt REST API
        1. Fetch the modifications from Scop3P REST API
        1. Run the data parsing code cells
        1. Run the "Functional scores" cell to visualise the plot
        
        ??? success "View functional scores"
            
            Plot extracted from the Colab notebook:
            
            <figure>
                <img src="../../assets/images/functional_sites.png" width="600" alt="Image on elixir landing page"/>
                <figcaption> P07949 functional sites </figcaption>
            </figure>

---

!!! warning "☕️ COFFEE BREAK"
    Time to grab a coffee or tea. We'll be back in ten minutes...

---

!!! note "To be continued: Go to chapter 5"
    [Next chapter](/../../chapters/chapter_05) explains how to connect PTMs to biophysical profiles.
