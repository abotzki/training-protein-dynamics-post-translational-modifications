This page is intended to help participants apply the concepts and workflows introduced in this course to their own proteins and research questions.

---

## 1.1 Biophysical properties

Biophysical properties such as early folding propensity, disorder probability, and backbone dynamics provide valuable complementary information to sequence and structure data. These features help researchers identify residues and regions that are important for protein folding, stability, and regulation.

By analysing these properties, it becomes possible to distinguish between regions that are structurally stable and regions that are flexible, transient, or condition-dependent. This distinction is especially relevant for signaling proteins, where function often depends on conformational changes rather than rigid structures.

### 1.1.1 Distribution channels of the B2BTools

There are multiple alternatives to use the predictors either locally or using cloud resources:

#### 1.1.1.1 Local installation

1. Via the Python Index (`pip`) [visit package page](https://pypi.org/project/b2bTools/): `pip install b2bTools`
1. Via the Conda package manager (`conda`) [visit package page](https://anaconda.org/channels/bioconda/packages/b2btools/overview): `conda install bioconda::b2btools`
1. Via containers (`biocontainers`) [visit containers page](https://biocontainers.pro/tools/b2btools): 
    1. Docker: `docker pull quay.io/biocontainers/b2btools:3.0.7--py310h8ea774a_2`
    1. Singularity: `singularity run https://depot.galaxyproject.org/singularity/b2btools:3.0.7--py310hdbdd923_0`.

#### 1.1.1.2 Cloud usage

1. Online Notebooks on Google Colab: [visit the public repository on Github](https://github.com/Bio2Byte/public_notebooks)
1. Using Galaxy platform for GUI oriented executions:
    1. Belgian server: [usegalaxy.be](https://usegalaxy.be/root?tool_id=toolshed.g2.bx.psu.edu/repos/iuc/b2btools_single_sequence/b2btools_single_sequence/3.0.5+galaxy0)
    1. European server: [usegalaxy.eu](https://usegalaxy.eu/root?tool_id=toolshed.g2.bx.psu.edu/repos/iuc/b2btools_single_sequence/b2btools_single_sequence/3.0.5+galaxy0)
    1. Australian server: [usegalaxy.org.au](https://usegalaxy.org.au/root?tool_id=toolshed.g2.bx.psu.edu/repos/iuc/b2btools_single_sequence/b2btools_single_sequence/3.0.5+galaxy0)

### 1.1.2 About Bio2Byte
This group is led by [Prof. Dr. Wim Vranken](https://bio2byte.be/people/31) and it is part of the [Vrije Universiteit Brussel](https://vub.be) in Belgium. 

Additional information about the Bio2Byte lab can be found at:

- Home page: [https://bio2byte.be](https://bio2byte.be)  
- Latest publications: [https://bio2byte.be/publications](https://bio2byte.be/publications)
- Tools: [https://bio2byte.be/tool/](https://bio2byte.be/tool/)
- Databases: [https://bio2byte.be/database/](https://bio2byte.be/database/)

## 1.2 Post-translational modifications (PTMs)

Post-translational modifications (PTMs) play a critical role in regulating protein activity, localization, interactions, and stability. Both **ScoP3P** [@ScoP3P] and **ScoP3PTM** aim to provide biological and structural context to these modifications, moving beyond simple site annotation.

### 1.2.1 ScoP3P

One of the most extensively studied PTMs is protein phosphorylation. Advances in high-throughput mass spectrometry (MS/MS) have led to a rapid increase in publicly available phosphoproteomics data. However, many existing phosphorylation resources focus mainly on sequence information and phosphosite positions, often lacking structural and biophysical context.

Structural information is particularly important when addressing a key biological question: how to distinguish functional phosphosites from non-functional or incidental ones.

ScoP3P is a database of human phosphosites derived from public proteomics data. Each phosphosite is annotated with detailed, residue-level structural and biophysical information using state-of-the-art prediction tools. The platform is available at:
https://iomics.ugent.be/scop3p/index

!!! success "P07949 example"

    Visit the entry page for the protein of interest on ScoP3P:
    https://iomics.ugent.be/scop3p/index?protein=P07949

    <figure>
        <img src="../../assets/images/follow_up_scop3p.jpg" width="1024" alt="P07949 on ScoP3P"/>
        <figcaption>P07949 on ScoP3P</figcaption>
    </figure>

!!! notes "REST API access"
    There are several endpoints to fetch the data Scop3P through HTTP methods. The API is documented using Swagger at [https://iomics.ugent.be/scop3p/swagger-ui/index.html](https://iomics.ugent.be/scop3p/swagger-ui/index.html).
    
    !!! question "P07949 REST API example"
    
        The modifications for P07949 can be found at [https://iomics.ugent.be/scop3p/api/modifications?accession=P07949](https://iomics.ugent.be/scop3p/api/modifications?accession=P07949):
        
        ??? success "Show JSON response"
            ```json
            {
                "proteinName": "Proto-oncogene tyrosine-protein kinase receptor Ret (EC 2.7.10.1) (Cadherin family member 12) (Proto-oncogene c-Ret) [Cleaved into: Soluble RET kinase fragment; Extracellular cell-membrane anchored RET cadherin 120 kDa fragment]",
                "entryName": "RET_HUMAN",
                "accession": "P07949",
                "url": "https://iomics.ugent.be/scop3p/index?protein=P07949",
                "modifications": [
                    {
                    "residue": "THR",
                    "name": "phosphorylation",
                    "evidence": null,
                    "position": 291,
                    "source": "PRIDE",
                    "reference": null,
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 1
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": null,
                    "position": 606,
                    "source": "PRIDE",
                    "reference": null,
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 1
                    },
                    {
                    "residue": "SER",
                    "name": "phosphorylation",
                    "evidence": "Combined",
                    "position": 696,
                    "source": "UP, PRIDE",
                    "reference": "PubMed:19369195",
                    "functionalScore": 0.6410382,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 1
                    },
                    {
                    "residue": "SER",
                    "name": "phosphorylation",
                    "evidence": null,
                    "position": 699,
                    "source": "PRIDE",
                    "reference": null,
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 1
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": "Experimental",
                    "position": 806,
                    "source": "UP",
                    "reference": "PubMed:14711813",
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 0
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": "Experimental",
                    "position": 809,
                    "source": "UP",
                    "reference": "PubMed:14711813",
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 0
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": "Experimental",
                    "position": 900,
                    "source": "UP",
                    "reference": "PubMed:14711813,PubMed:16928683",
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 0
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": "Experimental",
                    "position": 905,
                    "source": "UP",
                    "reference": "PubMed:20117004,PubMed:14711813,PubMed:16928683,PubMed:28846099,PubMed:16778204",
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 0
                    },
                    {
                    "residue": "TYR",
                    "name": "phosphorylation",
                    "evidence": "Experimental",
                    "position": 981,
                    "source": "UP",
                    "reference": "PubMed:14711813",
                    "functionalScore": null,
                    "uniprotId": null,
                    "accession": null,
                    "specificSinglyPhosphorylated": 0
                    }
                ]
            }
            ```

### 1.2.2 ScoP3PTM

ScoP3P is being extended into **ScoP3PTM**, a broader resource that covers multiple types of post-translational modifications. The platform has expanded from 36 to 539 projects, and the number of processed spectra has grown from 60.2 million to approximately 1 billion. In addition to phosphorylation, ScoP3PTM includes more than 117 different modification types.

!!! success "P07949 example"

    Visit the summary page for the protein of interest on ScoP3PTM:
    https://iomics.ugent.be/scop3ptm/P07949/summary

    <figure>
        <img src="../../assets/images/follow_up_scop3ptm.jpg" width="1024" alt="P07949 on ScoP3PTM"/>
        <figcaption>P07949 on ScoP3PTM</figcaption>
    </figure>

### 1.2.3. About CompOmics

The [CompOmics group](https://www.compomics.com), headed by Prof. Dr. Lennart Martens, is part of the Department of Biomolecular Medicine of the Faculty of Medicine and Health Sciences of Ghent University, and the VIB-UGent Center for Medical Biotechnology of VIB, both in Ghent, Belgium.

The group has its roots in Ghent, but has active members all over Europe, and specializes in the management, analysis and integration of high-throughput Omics data with an aim towards establishing solid data stores, processing methods and tools to enable downstream systems biology research.

## 1.3 Structural visualisations

Mol* (`/molstar/`) [@MolStar] is a widely used component for rendering and exploring three-dimensional macromolecular structures in the browser.

In addition, the MolViewSpec [@MolViewSpec] library (https://molstar.org/mol-view-spec/) allows users to describe molecular visual scenes using a simple, declarative language. These descriptions can then be loaded directly into the Mol* viewer, enabling reproducible and shareable structural visualizations.
