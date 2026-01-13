This chapter moves from theory to practice by predicting the “anatomy” of the protein at the level of its biophysical properties. Using the **B2BTools** suite, we will explore how different regions of the protein behave in terms of dynamics, structure, and flexibility.

!!! question "Chapter questions"

    1. How to use the B2BTools online platform to predict biophysical profiles for protein sequences ?
    2. How to find biophysical patterns using the platform ? 
    3. 

---

## 3.1 Biophysical profiles

This package [@b2btools] offers biophysical feature predictors for protein sequences as well as different file parses and other utilities to help you with your protein data analysis. If your input data consists on one or more sequences not aligned, we provide you with the Single Sequence mode. On the other hand, if your input is a Multiple Sequence Alignment (MSA), we provide the MSA mode. For NMR data, we have the predictor ShiftCrypt (out of the scope of this course).

| Predictor   | Description                          | Publication                          |
| :----------- | ------------------------------------ | :------------------------------------ |
| `DynaMine` [@dynamine]       | Fast predictor of protein backbone dynamics using only sequence information as input. The version here also predicts side-chain dynamics and secondary structure predictors using the same principle.  | [doi: 10.1038/ncomms3741](https://doi.org/10.1038/ncomms3741) |
| `DisoMine` [@disomine]      | Predicts protein disorder with recurrent neural networks not directly from the amino acid sequence, but instead from more generic predictions of key biophysical properties, here protein dynamics, secondary structure and early folding. | [doi: 10.1016/j.jmb.2022.167579](https://doi.org/10.1016/j.jmb.2022.167579) |
| `EFoldMine` [@efoldmine]    | Predicts from the primary amino acid sequence of a protein, which amino acids are likely involved in early folding events. | [doi: 10.1038/s41598-017-08366-3](https://doi.org/10.1038/s41598-017-08366-3) |
| `AgMata` [@agmata]    | Single-sequence based predictor of protein regions that are likely to cause beta-aggregation. | [doi: 10.1093/bioinformatics/btz912](https://doi.org/10.1093/bioinformatics/btz912) |
| `PSPer` [@psper]   | PSP (Phase Separating Protein) predicts whether a protein is likely to phase-separate with a particular mechanism involving RNA interacts (FUS-like proteins). It will highlight the regions in your protein that are involved mechanistically, and provide an overall score. | [doi: 10.1093/bioinformatics/btz274](https://doi.org/10.1093/bioinformatics/btz274) |
| `Shift Crypt` [@shiftcrypt]    | Auto-encoding NMR chemical shifts from their native vector space to a residue-level biophysical index | [doi: 10.1093/nar/gkaa391](https://doi.org/10.1093/nar/gkaa391)|

### 3.1.1 DynaMine

DynaMine predicts **local protein backbone dynamics** directly from the amino acid sequence. More specifically, it estimates how rigid or flexible each residue is expected to be in solution, based on fast (nanosecond-scale) backbone motions.

The predictor was trained on backbone order parameters derived from **NMR chemical shift data**, which reflect protein behaviour in solution rather than a single static structure. Because of this, DynaMine captures intrinsic conformational tendencies that are independent of a specific folded state.

The output is a per-residue numerical score:

- Higher values indicate rigid regions with a strong tendency to adopt stable conformations
- Lower values indicate flexible or dynamic regions

Backbone dynamics are **not equivalent to intrinsic disorder**. A residue may be flexible while still being part of a folded structure, and rigid residues are not guaranteed to be structured under all conditions. DynaMine scores should therefore be interpreted as **biophysical propensities**, not as absolute structural assignments.

Specifically, for the backbone propensity prediction, the range values are:

- **Values > 1.0**: Membrane spanning regions
- **Values > 0.80 and < 1.0**: Rigid conformations
- **Values > 0.69 and < 0.80**: Context dependent
- **Values < 0.69**: Flexible regions

!!! notes "Backbone plot example"
    <figure>
        <img src="../../assets/images/P08100_backbone.jpg" width="1048" alt="P07949 on Scop3P"/>
        <figcaption>DynaMine backbone dynamics for P08100</figcaption>
    </figure>

### 3.1.2 DisoMine

DisoMine predicts **intrinsic disorder**, defined as regions of a protein that do not adopt a stable three-dimensional structure under physiological conditions.

The model was trained on experimentally annotated disordered regions from curated datasets and predicts disorder at the residue level. Unlike many disorder predictors, DisoMine does not rely directly on amino acid composition or evolutionary profiles. Instead, it uses predicted biophysical properties—such as backbone dynamics, secondary structure propensity, and early folding behaviour—as input.

The output is a probability score between 0 and 1:

- Higher values indicate a higher likelihood that the residue is intrinsically disordered
- Lower values indicate a tendency toward structured behaviour

DisoMine is particularly effective at identifying **long disordered regions**. The predictions are probabilistic and context-dependent: a high disorder score does not imply permanent disorder in all conditions, but rather a strong tendency to remain flexible or unstructured.

The threshold for this prediction is:

- **Above 0.5**: likely a disordered position
- **Below**: unlikely a disordered position


!!! notes "Disorder plot example"
    <figure>
        <img src="../../assets/images/P08100_disorder.jpg" width="1048" alt="DisoMine disorder propensities for P08100"/>
        <figcaption>DisoMine disorder propensities for P08100</figcaption>
    </figure>

### 3.1.3 EFoldMine

EFoldMine predicts **early folding residues**, defined as amino acids that are likely to form stable local structure at the very beginning of the protein folding process.

The predictor was trained using experimental data derived from hydrogen–deuterium exchange experiments, which identify residues that gain protection early during folding. EFoldMine therefore focuses on **folding kinetics**, rather than final structure.

The output highlights residues with high early folding propensity:

- These residues are likely to initiate local structure formation
- They may play a key role in guiding the folding pathway

Early folding residues are not necessarily rigid, conserved, or part of the final folded core. EFoldMine does not predict folding rates or final stability, but rather identifies **sequence-encoded folding initiation signals** that act early in the folding process.

The threshold for this prediction is:

- **Values > 0.169**: indicate residues that are likely to start the protein folding process
- **Below**: indicate residues that are unlikely to start the protein folding process


!!! notes "EFoldMine plot example"
    <figure>
        <img src="../../assets/images/P08100_efoldmine.jpg" width="1048" alt="DisoMine disorder propensities for P08100"/>
        <figcaption>EFoldMine early folding events for P08100</figcaption>
    </figure>


### 3.1.4 AgMata

AgMata predicts **beta-sheet aggregation propensity** from single protein sequences. It identifies regions that are intrinsically prone to form intermolecular beta-sheet interactions, a key feature of amyloid-like aggregation.

Unlike many aggregation predictors, AgMata is not directly trained on known aggregating sequences. Instead, it uses a generalized statistical potential that integrates predicted biophysical properties, including backbone dynamics and secondary structure tendencies.

The output highlights regions with increased aggregation risk:

- Higher values indicate a stronger intrinsic tendency toward beta-aggregation
- Lower values indicate reduced aggregation propensity
- Peaks indicate residues likely to be involved in beta-sheet aggregation.

AgMata predictions reflect **intrinsic sequence-level risk**, not actual aggregation outcomes. Cellular context, protein concentration, interaction partners, and chaperones are not considered. The predictor is most informative when interpreted together with disorder and dynamics predictions.

!!! notes "AgMata plot example"
    <figure>
        <img src="../../assets/images/P08100_agmata.jpg" width="1048" alt="DisoMine disorder propensities for P08100"/>
        <figcaption>AgMata beta-aggregation for P08100</figcaption>
    </figure>

!!! warning "AgMata takes longer to predict the peaks"
    Some of the activities will skip this predictor.

## 3.2 Extracting the protein sequence

The first step is to download the protein sequence in FASTA format.

!!! example "Hands-on: P07949 canonical sequence"

    1. Download the **canonical protein sequence** from UniProtKB. 
    1. Visit the official UniProtKB website, locate the protein entry.
    1. Download the FASTA sequence from the contextual menu.

    ??? success "Solution"

        The following FASTA sequence corresponds to the protein of interest and was retrieved from
        [https://rest.uniprot.org/uniprotkb/P07949.fasta](https://rest.uniprot.org/uniprotkb/P07949.fasta):

        ```bash
        >sp|P07949|RET_HUMAN Proto-oncogene tyrosine-protein kinase receptor Ret OS=Homo sapiens OX=9606 GN=RET PE=1 SV=3
        MAKATSGAAGLRLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRDAP
        EEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSVRNRGFPLLT
        ...
        DGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
        ```

        :fontawesome-regular-floppy-disk: You should now have the file `P07949.fasta` available in your working environment.
        
        ```text
        ./training-data-directory
        └─── P07949.fasta
        ```

## 3.3 Analysing single sequences (_standalone_ mode)

As mentioned earlier, the **B2BTools** suite provides several predictors to analyse protein biophysical properties:

- Backbone and side-chain dynamics (via **DynaMine**)
- Intrinsically disordered residues (via **DisoMine**)
- Early folding regions (via **EFoldMine**)
- Beta-aggregation-prone regions (via **AgMata**)

The Bio2Byte lab provides an online platform [@b2btools-webserver] to run the biophysical predictions described above for proteins of interest. The platform is available at:
[https://bio2byte.be/online_predictors/](https://bio2byte.be/online_predictors/) (this resource is still under active development, and user feedback is highly appreciated. A previous version of the platform is available at: https://bio2byte.be/b2btools).

!!! warning "Attention: Required token"
    
    First of all, write down in your notes a personal alphanumeric **TOKEN** to enable job submission and later retrieval of results on the B2BTools platform.
    
    1. Access the [B2BTools platform](https://bio2byte.be/online_predictors/) and set your token.
    2. The token will be saved in your browser internal storage and remembered every time you access again the website.
    
    ??? question "Where is the TOKEN textbox?"
        <figure>
            <img src="../../assets/images/chapter_02_token.jpg" width="800" alt="Token input example"/>
            <figcaption>Notice the input textbox for your TOKEN</figcaption>
        </figure>
    
!!! example "Hands-on: Predicting the biophysical features"

    1. Select the **Single Sequence** analysis type and upload your FASTA file.  
    1. Submitted jobs can be accessed from the **Token results** page:
    [https://bio2byte.be/online_predictors/past-results/](https://bio2byte.be/online_predictors/past-results/).
    1. Locate your job and open the corresponding results page.
    
    ??? success "Solution"
    
        1. You will be able to find the results inside the "Single Sequence Predictions" table. 
        1. Your job will have an action button "View Results" that opens a link like `https://bio2byte.be/online_predictors/results/UUID/`.

### 3.3.1 Understanding the results as biological profiles

#### 3.3.1.1 Exploring intrinsic flexibility and folding propensity

#### 3.3.1.2 Visualization of biophysical profiles

---

!!! warning "☕️ COFFEE BREAK"
    Time to grab a coffee or tea. We'll be back in ten minutes...

---

## 3.4 Multiple sequence alignments (MSA)

To fully exploit the predictive power of biophysical tools, it is useful to study the target protein in the context of related proteins. Comparing similar sequences allows the identification of conserved biophysical profiles as well as positions that show divergence across homologs.

### 3.4.1 Working with the aligned kinase domain

In the following hands-on activities the focus will be on the homolog kinase domains of the P07949's 90%-similarity proteins. 

### 3.4.1.1 Fetching the similar proteins

UniProtKB provides access to similar proteins directly from the protein entry page, in the **Similar proteins** section.

!!! example "Hands-on: Getting the 90%-identity protein sequences"

    Open the protein entry in UniProtKB and locate the **Similar proteins** table at:
    [https://www.uniprot.org/uniprotkb/P07949/entry#similar_proteins](https://www.uniprot.org/uniprotkb/P07949/entry#similar_proteins).

    Select the entries with 90% sequence identity and choose to view all results in UniProtKB.

    Exclude other human proteins and short sequences to retain proteins with lengths between 1000 and 1120 amino acids.  
    Once the entries are selected, download the canonical sequences using the **Download** option in FASTA format, without compression.

    Before proceeding with the alignment, add the `P07949` sequence at the top of the downloaded FASTA file.

    ??? success "Solution"

        The canonical sequences can be retrieved from the following [UniProtKB REST endpoint](https://rest.uniprot.org/uniprotkb/stream?download=true&format=fasta&query=accession%3AA0A0D9REZ9+OR+accession%3AA0A2I2ZX13+OR+accession%3AA0A2I3H8C4+OR+accession%3AA0A2I3LXM4+OR+accession%3AA0A2I3TR47+OR+accession%3AA0A2J8IX92+OR+accession%3AA0A2J8IX93+OR+accession%3AA0A2J8XTA5+OR+accession%3AA0A2K5HW95+OR+accession%3AA0A2K5MKU6+OR+accession%3AA0A2K5V8L5+OR+accession%3AA0A2K5YH50+OR+accession%3AA0A2K6CCS4+OR+accession%3AA0A2K6R0I7+OR+accession%3AA0A2R9AWY2+OR+accession%3AA0A2R9B0Q5+OR+accession%3AA0A7N9CS34+OR+accession%3AA0A8C9HBV6+OR+accession%3AA0A8D2EQF8+OR+accession%3AF6S299+OR+accession%3AF6S7W7+OR+accession%3AG1S142+OR+accession%3AG3QLZ3+OR+accession%3AH2NA70+OR+accession%3AH2Q1T9+OR+accession%3AH9ZBZ9+OR+accession%3AH9ZC00).

        The FASTA file contains all the sequences: 
        
        ```shell
        >tr|A0A0D9REZ9|A0A0D9REZ9_CHLSB Proto-oncogene tyrosine-protein kinase receptor Ret OS=Chlorocebus sabaeus OX=60711 GN=RET PE=3 SV=1
        LTSLLPTVALGLYFSRDAYWEKLYVDQPAGTPLLYVHALRDAPEEVPSFRLGQHLYGTYR
        TRLHENNWICIQEDTGLLYLNRSLDRSSWEKLSGRNRGFPLLTVYLKVFLSPTFLREGEC
        ...
        YANWMLSPSAAKLMDTFDS
        
        >tr|A0A2K5MKU6|A0A2K5MKU6_CERAT Proto-oncogene tyrosine-protein kinase receptor Ret OS=Cercocebus atys OX=9531 GN=RET PE=3 SV=1
        MAKATSGAAGLRLLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQPAGTPLLYVHALRDS
        PEEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSGRNRGFPLL
        ...
        ADGTNTGFPRYANDSVYANWMLSPSAAKLMDTFDS
        ...
        
        >tr|H9ZC00|H9ZC00_MACMU Proto-oncogene tyrosine-protein kinase receptor Ret OS=Macaca mulatta OX=9544 GN=RET PE=2 SV=1
        MAKATSGAAGLRLLLLLLLLPLLGKGALGLYFSRDAYWEKLYVDQPAGTPLLYVHALRDA
        PEEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDRSSWEKLSGRNRGFPLL
        ...
        ASTPSDSLLYDDGLSEEETPLVDCNNAPLPRALPSTWIENKLYGRISHAFTRF
        ```

        :fontawesome-regular-floppy-disk: You should now have the file `P07949.90-similar.fasta` available in your working environment.
        
        ```text
        ./training-data-directory
        │─── P07949.fasta
        └─── P07949.90-similar.fasta
        ```

### 3.4.1.2 Building the MSA

To continue this activity, the multiple sequence alignment (MSA) will be generated using the online **Clustal Omega** server provided by EMBL-EBI.

!!! example "Hands-on: Aligning the sequences"

    1. Open the Clustal Omega submission form at:
    [https://www.ebi.ac.uk/jdispatcher/msa/clustalo](https://www.ebi.ac.uk/jdispatcher/msa/clustalo).
    1. Upload the file `P07949.90-similar.fasta` as input.  
    1. Request the output format as **Pearson/FASTA** and keep the original sequence order by setting the **order** option to *input*.
    1. Set the job title to `P07949.90-similar.msa`.

    ??? success "Solution"

        After the job has completed on the EMBL-EBI servers, you will be redirected to the results page.  
        This page contains several tabs for exploring the alignment.

        From the **Tool output** tab, download the MSA by clicking the blue **Download** button.

        Example of the aligned P07949 protein sequence:

        ```
        >sp|P07949|RET_HUMAN Proto-oncogene tyrosine-protein kinase receptor Ret OS=Homo sapiens OX=9606 GN=RET PE=1 SV=3
        MAKATSGAAGLRLLLL--LLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRD
        ...
        LKQVNHPHVIKLYGACSQD--GPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSS
        ...
        LTRADGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
        ```

        :fontawesome-regular-floppy-disk: You should now have the file `P07949.90-similar.msa.fasta` available in your working environment.
        
        ```text
        ./training-data-directory
        │─── P07949.fasta
        │─── P07949.90-similar.fasta
        └─── P07949.90-similar.msa.fasta
        ```

### 3.4.1.3 Extracting the domain of interest

The next step is to focus the analysis on the kinase domain positions across all aligned sequences. For this purpose, the course provides a Google Colab notebook that runs a Python script to identify and extract the aligned positions corresponding to a defined amino acid range in the original reference sequence.

!!! warning "Attention: Google Account required"
    
    You must log in using a Google account to run the code in this notebook. By default, you can use your "@gmail.com" address.

!!! example "Hands-on: Extracting the aligned domain from the MSA"

    1. Open the [Google Colab notebook](https://colab.research.google.com/drive/16GakNh96qJcQFqvl9bUwC_1F5ZpZHGWb?usp=sharing) related to this activity.
    1. The notebook is divided into two main sections.  
    1. First, run the **four hidden cells** in the section *Dependencies and method definitions* by clicking the **Run** icon. This step loads the required Python libraries and helper functions into memory.
    1. Next, move to the *Usage* section and execute the cells in order.  
    1. The first cell will prompt you to upload the alignment file `P07949.90-similar.msa.fasta`.
    1. After the file is uploaded, fill in the fields in the *Extraction parameters* cell and click the **Run** icon to start the extraction.
    1. Once the execution is complete, download the output file from the **Files** panel to your local working environment.

    ??? success "Solution"

        1. Use the following parameters in the *Extraction parameters* cell, based on the kinase domain definition:
            - `uniprot_id`: `P07949`
            - `start_pos`: `724`
            - `end_pos`: `1016`
            - `max_gap_fraction`: `0.4` (40%)
            - `output_filename`: `P07949.90-similar.msa.kinase.fasta`
        1. Save the file from the **Files** panel on the left navigation (folder icon), locate the file, open the contextual menu, and select **Download**.

        ??? notes "Output console message"
            After running the cell, a new file will be generated and a summary message similar to the one below will be displayed:

            ```bash
            Parameters:
            UniProt ID: P07949
            Start Position: 724
            End Position: 1016
            Max Gap Fraction: 0.4
            For sp|P07949|RET_HUMAN: found 0.006779661016949152 as gap fraction (seq len: 295)
            For tr|A0A0D9REZ9|A0A0D9REZ9_CHLSB: found 0.0 as gap fraction (seq len: 295)
            ...
            File P07949.90-similar.msa.kinase.fasta written using alignment columns: 725 and 1020 (295 residues)
            ```

        ??? notes "Kinase sequences"
        
            The extracted alignment will start as follows: 
            ```
            >sp|P07949|RET_HUMAN Proto-oncogene tyrosine-protein kinase receptor Ret OS=Homo sapiens OX=9606 GN=RET PE=1 SV=3
            LVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPSELRDLLSEFNVLKQVN
            HPHVIKLYGACSQD--GPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSSSLDHP
            ...
            NLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKRRDYL
            
            >tr|A0A0D9REZ9|A0A0D9REZ9_CHLSB Proto-oncogene tyrosine-protein kinase receptor Ret OS=Chlorocebus sabaeus OX=60711 GN=RET PE=3 SV=1
            LVLGKTLGEGEFGKVVKATAFRLKGRAGYTTVAVKMLKENASPSELRDLLSEFNLLKQVN
            HPHVIKLYGACSQDAPGPLLLIVEYAKYGSLRGFLRESRKVGPGYLGSGGSRNSSSLDHP
            ...
            NLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISKDLEKMMVKSRDYL
            ```    
        :fontawesome-regular-floppy-disk: You should now have the file `P07949.90-similar.msa.kinase.fasta` available in your working environment.
        
        ```text
        ./training-data-directory
        │─── P07949.fasta
        │─── P07949.90-similar.fasta
        │─── P07949.90-similar.msa.fasta
        └─── P07949.90-similar.msa.kinase.fasta
        ```

### 3.4.1.4 Predicting the biophysical features

We are now ready to predict the aligned biophysical features using **B2BTools**.

!!! example "Hands-on: Predicting the aligned biophysical features for the kinase domain"

    1. Open a new browser tab and go to the online platform at:
    https://bio2byte.be/online_predictors
    1. This time, select **Multiple Sequence Alignment** as the analysis type instead of **Single Sequence**.  
    Upload the file `P07949.90-similar.msa.kinase.fasta` and submit the job.
    1. After submission, you will be redirected to the **Token results** page.

    ??? success "Solution"

        1. Once the prediction job has completed, the results will appear in the **MSA Predictions** table. It takes approximately less than two minutes to finish.
        1. Click the **View Results** button to open the results page for the aligned kinase domain.

### 3.4.2 Understanding the results as biological profiles

#### 3.3.2.1 Exploring intrinsic flexibility and folding propensity

#### 3.3.2.2 Visualization of biophysical profiles

TBC

## 3.5 Connecting online resources

For a selected protein, a set of "external resources" will be shown in the left navigation bar if the header is recognised as a UniProt entry.

!!! example "Hands-on: Finding phosphosites on Scop3P for P07949"

    1. Look for all the modified kinases on Scop3P at https://iomics.ugent.be/scop3p/search?q=kinase.
    1. Find and select `P07949` from the list. 
    
    Given the B2BTools page also includes the direct link, you can proceed with these steps: 
    
    1 Select the `P07949` protein in the dropdown selector.
    1. Clicking on the "Find PTMs on Scop3P" redirects you to the entry page on that resource: [https://iomics.ugent.be/scop3p/index?protein=P07949](https://iomics.ugent.be/scop3p/index?protein=P07949).

    ??? success "Solution"
        <figure>
            <img src="../../assets/images/follow_up_scop3p.jpg" width="800" alt="P07949 on Scop3P"/>
            <figcaption>P07949 on Scop3P</figcaption>
        </figure>
        
---

!!! warning "🥪 LUNCH BREAK"
    Time to grab a coffee or tea. We'll be back in one and a half hour...

---


!!! note "To be continued: : Go to chapter 4"
    [Next chapter](/../../chapters/chapter_04) explains how to explore the modifications (PTMs).
