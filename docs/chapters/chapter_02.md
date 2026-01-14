!!! question "Chapter questions"

    1. How can protein biophysical properties help us understand function beyond what is visible from a static structure?
    2. Which regions of a signaling protein, such as a receptor tyrosine kinase, are most likely to be functionally regulated by dynamics or disorder?
    3. How can sequence conservation and divergence across species inform us about essential versus adaptable protein regions?
    4. Why might post-translational modifications preferentially occur in specific biophysical or structural contexts?
    5. How can mutations alter protein behaviour without strongly affecting the overall folded structure?
    6. What are the limitations of studying proteins using a single reference sequence or a single predicted structure?

---

## 2.1 The target protein **P07949**

This course is focused on the "Proto-oncogene tyrosine-protein kinase receptor Ret" protein associated to the gene "RET" of homo sapiens. 

!!! notes "Subcellular location"
    
    Based on the information extracted from UniProt, this protein can be found in:
    
    1. The cell membrane, the selectively permeable membrane which separates the cytoplasm from its surroundings: Single-pass type I membrane protein
    1. The membrane surrounding the endosome: Single-pass type I membrane protein
    
    Note: Predominantly located on the plasma membrane (PubMed:23333276, PubMed:9575150). In the presence of SORL1 and GFRA1, directed to endosomes (PubMed:23333276).

This protein has a sequence length of 1114 amino acids. It can be found in UniProtKB [@UniProtConsortium] under the accession number [**P07949**](https://www.uniprot.org/uniprotkb/P07949/entry) or the entry name [**RET_HUMAN**](https://www.uniprot.org/uniprotkb/P07949/entry).

!!! notes "Crystal structure 2IVS"
    
    ??? success 'View 2IVS'
    
        <iframe src="https://molstar.org/viewer/?pdb=2IVS&&hide-controls=1" height="600" width="100%" title="Protein Data Bank in Europe Knowledge Base - Entry 2IVS"></iframe>

        _[2IVS](https://www.ebi.ac.uk/pdbe/pdbe-kb/proteins/2IVS): Crystal structure of non-phosphorylated ret tyrosine kinase domain (Protein Data Bank in Europe Knowledge Base)_

According to the functional annotation provided by UniProt, this protein plays a central role in several cellular processes:

> - This protein is a receptor tyrosine-protein kinase involved in numerous cellular mechanisms including cell proliferation, neuronal navigation, cell migration, and cell differentiation in response to glia cell line-derived growth family factors (GDNF, NRTN, ARTN, PSPN and GDF15). In contrast to most receptor tyrosine kinases, RET requires not only its cognate ligands but also coreceptors, for activation. 
> - It acts as a dependence receptor via the GDNF-GFRA1 signaling: in the presence of the ligand GDNF in somatotrophs within pituitary, promotes survival and down regulates growth hormone (GH) production, but triggers apoptosis in absence of GDNF.
> - It is required for the molecular mechanisms orchestration during intestine organogenesis via the ARTN-GFRA3 signaling: involved in the development of enteric nervous system and renal organogenesis during embryonic life, and promotes the formation of Peyer's patch-like structures, a major component of the gut-associated lymphoid tissue (By similarity).
> - It mediates, through interaction with GDF15-receptor GFRAL, GDF15-induced cell-signaling in the brainstem which triggers an aversive response, characterized by nausea, vomiting, and/or loss of appetite in response to various stresses.
> - It modulates cell adhesion via its cleavage by caspase in sympathetic neurons and mediates cell migration in an integrin (e.g. ITGB1 and ITGB3)-dependent manner.
> - Also, it is active in the absence of ligand, triggering apoptosis through a mechanism that requires receptor intracellular caspase cleavage.
> - It triggers the differentiation of rapidly adapting (RA) mechanoreceptors.
> - **It phosphorylates PTK2/FAK1.**

!!! notes "Crystal structure 6NJA"
    ??? success "View 6NJA"
        <iframe src="https://molstar.org/viewer/?pdb=6NJA&&hide-controls=1" height="600" width="100%" title="Protein Data Bank in Europe Knowledge Base - 6NJA entry"></iframe>

        _[6NJA](https://www.ebi.ac.uk/pdbe/pdbe-kb/proteins/6NJA): Crystal structure of phosphorylated ret tyrosine kinase domain (Protein Data Bank in Europe Knowledge Base)_

## 2.2 The target Kinase domain

In this training, we will focus on a specific protein domain: the kinase domain, located approximately between positions 724 and 1016 of the protein sequence.

!!! info "Protein Kinase domain sequence: range 724 to 1016"

    Here you can find the domain sequence in FASTA format ([PROSITE-ProRule: PRU00159](https://prosite.expasy.org/rule/PRU00159)).

    ??? success "View sequence"
    
        ```fasta
        LVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPSELRDLLSEFNVLKQV
        NHPHVIKLYGACSQDGPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSSSLDHP
        DERALTMGDLISFAWQISQGMQYLAEMKLVHRDLAARNILVAEGRKMKISDFGLSRDVY
        EEDSYVKRSQGRIPVKWMAIESLFDHIYTTQSDVWSFGVLLWEIVTLGGNPYPGIPPER
        LFNLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKRRDYL
        ```
    
    ??? success "View predicted model AF-P07949-F1-v6"
        <iframe src="https://molstar.org/viewer/?afdb=P07949&&hide-controls=1" height="600" width="100%" title="AlphaFold predicted model"></iframe>
        
        _The predicted model [`AF-P07949-F1-v6`](https://alphafold.ebi.ac.uk/entry/AF-P07949-F1) by AlphaFold Protein Structure Database._

## 2.3 Structural overview

> MolViewStories is a powerful web application that lets you create beautiful, interactive molecular visualizations. Whether you’re a researcher, educator, or student, MolViewStories helps you tell compelling scientific stories using 3D molecular structures.

This story shows the different structures related to RET protein (P07949) focusing on the kinase domain:

<iframe src="https://molstar.org/stories-viewer/v1?story-id=d21ff556&data-format=mvsx" style="width:1280px; height:720px; border:none;" title="Mol* Stories Viewer" allow="autoplay"></iframe>

---

!!! note "To be continued: Go to chapter 3"
    [Next chapter](/../../chapters/chapter_03) explains how to predict biological profiles.
