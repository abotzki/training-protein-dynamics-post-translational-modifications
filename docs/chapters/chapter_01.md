Welcome to this VIB training. The authors of this course designed a full teaching day that combines theory with hands-on activities, allowing participants to apply the concepts in practice.

---

## 1.1 Introducing the training methodology

The protein of interest for this training is the human **proto-oncogene tyrosine-protein kinase receptor RET**, encoded by the **RET** gene. 

!!! info "Protein sequence"

    Although the UniProt entry describes two isoforms, produced by alternative splicing, this course is based on the canonical sequence in FASTA format: **P07949-1** ([P07949 · RET_HUMAN](https://www.uniprot.org/uniprotkb/P07949/)).

    ??? success "View sequence"
    
        ```
        >sp|P07949|RET_HUMAN Proto-oncogene tyrosine-protein kinase receptor Ret OS=Homo sapiens OX=9606 GN=RET PE=1 SV=3
        MAKATSGAAGLRLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRDAP
        EEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSVRNRGFPLLT
        VYLKVFLSPTSLREGECQWPGCARVYFSFFNTSFPACSSLKPRELCFPETRPSFRIRENR
        PPGTFHQFRLLPVQFLCPNISVAYRLLEGEGLPFRCAPDSLEVSTRWALDREQREKYELV
        AVCTVHAGAREEVVMVPFPVTVYDEDDSAPTFPAGVDTASAVVEFKRKEDTVVATLRVFD
        ADVVPASGELVRRYTSTLLPGDTWAQQTFRVEHWPNETSVQANGSFVRATVHDYRLVLNR
        NLSISENRTMQLAVLVNDSDFQGPGAGVLLLHFNVSVLPVSLHLPSTYSLSVSRRARRFA
        QIGKVCVENCQAFSGINVQYKLHSSGANCSTLGVVTSAEDTSGILFVNDTKALRRPKCAE
        LHYMVVATDQQTSRQAQAQLLVTVEGSYVAEEAGCPLSCAVSKRRLECEECGGLGSPTGR
        CEWRQGDGKGITRNFSTCSPSTKTCPDGHCDVVETQDINICPQDCLRGSIVGGHEPGEPR
        GIKAGYGTCNCFPEEEKCFCEPEDIQDPLCDELCRTVIAAAVLFSFIVSVLLSAFCIHCY
        HKFAHKPPISSAEMTFRRPAQAFPVSYSSSGARRPSLDSMENQVSVDAFKILEDPKWEFP
        RKNLVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPSELRDLLSEFNVLK
        QVNHPHVIKLYGACSQDGPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSSSLDH
        PDERALTMGDLISFAWQISQGMQYLAEMKLVHRDLAARNILVAEGRKMKISDFGLSRDVY
        EEDSYVKRSQGRIPVKWMAIESLFDHIYTTQSDVWSFGVLLWEIVTLGGNPYPGIPPERL
        FNLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKRRDYLDLAA
        STPSDSLIYDDGLSEEETPLVDCNNAPLPRALPSTWIENKLYGMSDPNWPGESPVPLTRA
        DGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
        ```

1. We will predict biophysical features for this protein using the Bio2Byte online platform, specifically the **B2BTools** suite. To enable a deeper analysis of these biophysical properties, we will generate a multiple sequence alignment (MSA) of sequences sharing at least 90% identity. This alignment will be used to identify conserved and variable patterns across homologous sequences.
1. The MSA will be created using **Clustal Omega**, and the aligned kinase domain will be extracted using a **Google Colab** notebook.
1. Post-translational modifications (PTMs) for the protein of interest will be explored using the **Scop3P** online platform, which is directly linked from the B2BTools prediction results. After analyzing the available information on modifications, structures, and experimental evidence, we will follow a more detailed protocol to link biophysical patterns with PTMs.
1. Finally, the course will address the impact of mutations. We will show how to modify the wild-type sequence and assess the effect of single amino acid substitutions on biophysical profiles and predicted protein structures using **AlphaFold v3**.

## 1.2 ELIXIR Belgium node services used in this training

Belgium is part of the ELIXIR Europe network as a National Node. The Belgian node, [ELIXIR Belgium](https://www.elixir-belgium.org/), provides both federal-level services and local initiatives, including research infrastructure, domain-specific services, training activities, and workshops.

<figure>
    <img src="../../assets/images/ELIXIR_BELGIUM.png" width="200" alt="ELIXIR Belgium"/>
    <figcaption>ELIXIR Belgium</figcaption>
</figure>

This course focuses on two bioinformatics tools and resources: **B2BTools**, used to predict and analyse protein biophysical features, and **Scop3P**, used to explore post-translational modifications (PTMs).

### 1.2.1 Introduction to Bio2Byte Tools

**DynaMine** [@dynamine] is a predictor specifically designed to estimate protein backbone dynamics. Backbone dynamics are related to, but not the same as, protein disorder. DynaMine was trained using values derived from NMR chemical shift data and therefore captures protein movements in solution. Its training set includes both fully folded proteins and intrinsically disordered proteins.

The **B2BTools** tool suite [@b2btools] extends the original DynaMine predictor by including several predictors developed by the Bio2Byte lab.

In addition to backbone dynamics, it provides predictions for side-chain dynamics and conformational preferences (alpha helix, beta sheet, and coil), all derived from NMR data and trained using the same methodology. The platform also includes predictors for early folding regions (**EFoldMine**) [@efoldmine], beta-sheet aggregation (**AgMata**) [@agmata], and protein disorder (**DisoMine**) [@disomine].

### 1.2.2 Introduction to Scop3P (and Scop3PTM)

Scop3P [@Scop3P], developed at Ghent University and available online since June 2019, is a dedicated resource to explore and interpret the impact of phosphorylation sites on human protein structure and function. It supports researchers in analysing individual phosphosites or phosphoproteins within a structural, biophysical, and biological context.

The resource integrates public data from several major international databases, including UniProtKB and the Protein Data Bank (PDB). In addition, it incorporates reprocessed mass spectrometry-based phosphoproteomics data from PRIDE/ProteomeXchange. These datasets are collected worldwide, making Scop3P a strongly international and community-driven resource.

!!! success "About the future of Scop3P and the development of Scop3PTM"
    **Scop3P is being extended to Scop3PTM**
    
    - Scop3PTM integrates information from diﬀerent knowledge bases and shows how re-analysis of large scale public proteomics data sets can add an additional level of significance and confidence to the PTM-sites.
    - Scop3PTM system will provide a unique and powerful resource to understand the impact of PTM-sites on human protein structure-function relationship.
    
    Beta access is available at [https://iomics.ugent.be/scop3ptm/](https://iomics.ugent.be/scop3ptm/).

---

!!! note "Let's get started: Go to chapter 2"
    [Next chapter](/../../chapters/chapter_02) explains the biological context.
