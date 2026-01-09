!!! question "Chapter questions"

    1. How can biophysical predictions help to interpret the functional impact of phosphosites?
    2. How to evaluate the impact of mutations using these tools?
    
## 4.1 Evaluating the impact of a mutation

Following up this activity, the Mutation table of the Scop3P entry page shows different types of mutations. Let's focus on the "Disease" type to select the mutation E768D that mutates a Glutamic Acid (Glu, E) at the position 768, inside the Kinase domain, to a Aspartic Acid (Asp, D). 

!!! example "Hands-on: Manually create the variant sequence"

    Edit the position 768 of the wild type canonical sequence from the `P07949.fasta` file to replace the "E" with a "D" and save it as a `P07949.E768D.fasta`.

    ??? success "Solution"

        This is an variant sequence in FASTA format:
        
        ~~~
        >sp|P07949| Variant E768D - RET_HUMAN Proto-oncogene tyrosine-protein kinase receptor Ret OS=Homo sapiens OX=9606 GN=RET PE=1 SV=3
        MAKATSGAAGLRLLLLLLLPLLGKVALGLYFSRDAYWEKLYVDQAAGTPLLYVHALRDA
        PEEVPSFRLGQHLYGTYRTRLHENNWICIQEDTGLLYLNRSLDHSSWEKLSVRNRGFPL
        LTVYLKVFLSPTSLREGECQWPGCARVYFSFFNTSFPACSSLKPRELCFPETRPSFRIR
        ENRPPGTFHQFRLLPVQFLCPNISVAYRLLEGEGLPFRCAPDSLEVSTRWALDREQREK
        YELVAVCTVHAGAREEVVMVPFPVTVYDEDDSAPTFPAGVDTASAVVEFKRKEDTVVAT
        LRVFDADVVPASGELVRRYTSTLLPGDTWAQQTFRVEHWPNETSVQANGSFVRATVHDY
        RLVLNRNLSISENRTMQLAVLVNDSDFQGPGAGVLLLHFNVSVLPVSLHLPSTYSLSVS
        RRARRFAQIGKVCVENCQAFSGINVQYKLHSSGANCSTLGVVTSAEDTSGILFVNDTKA
        LRRPKCAELHYMVVATDQQTSRQAQAQLLVTVEGSYVAEEAGCPLSCAVSKRRLECEEC
        GGLGSPTGRCEWRQGDGKGITRNFSTCSPSTKTCPDGHCDVVETQDINICPQDCLRGSI
        VGGHEPGEPRGIKAGYGTCNCFPEEEKCFCEPEDIQDPLCDELCRTVIAAAVLFSFIVS
        VLLSAFCIHCYHKFAHKPPISSAEMTFRRPAQAFPVSYSSSGARRPSLDSMENQVSVDA
        FKILEDPKWEFPRKNLVLGKTLGEGEFGKVVKATAFHLKGRAGYTTVAVKMLKENASPS
        DLRDLLSEFNVLKQVNHPHVIKLYGACSQDGPLLLIVEYAKYGSLRGFLRESRKVGPGY
        LGSGGSRNSSSLDHPDERALTMGDLISFAWQISQGMQYLAEMKLVHRDLAARNILVAEG
        RKMKISDFGLSRDVYEEDSYVKRSQGRIPVKWMAIESLFDHIYTTQSDVWSFGVLLWEI
        VTLGGNPYPGIPPERLFNLLKTGHRMERPDNCSEEMYRLMLQCWKQEPDKRPVFADISK
        DLEKMMVKRRDYLDLAASTPSDSLIYDDGLSEEETPLVDCNNAPLPRALPSTWIENKLY
        GMSDPNWPGESPVPLTRADGTNTGFPRYPNDSVYANWMLSPSAAKLMDTFDS
        ~~~

Following up, the predicted model by AlphaFold can be accessed directly from the AlphaFold Protein Structure Database. 

!!! example "Hands-on: Downloading the AlphaFold predicted model"

    Visit the [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk) and query the canonical structure by UniProt ID.
    
    Download the structure in mmCIF format (`.cif` extension) to your working environment.
    
    ??? success "Solution"
    
        The canonical predicted structure is available on [https://alphafold.ebi.ac.uk/entry/AF-P07949-F1](https://alphafold.ebi.ac.uk/entry/AF-P07949-F1).
        
To evaluate the impact at biophysical level as well as structural conformation, the next step is to predict the variant structure using AlphaFold 3 server. 

!!! warning "Google account required"
    You must log in using a Google account to enqueue structural prediction jobs. By default, you can use your "@gmail.com" address.

!!! example "Hands-on: Predicting the variant structure for the mutant protein"

    Open the AlphaFold Server at [https://alphafoldserver.com](https://alphafoldserver.com) and log in using your Google Account. By default you are entitled with 30 jobs. 
    
    Add the protein entry in the "Server" form with a single copy. Continue and preview the job to submit it as "P07949_E768D".

    ??? success "Solution"

        The enqueued job will be listed in the jobs table below the "Continue and review job" blue button. Once the job is completed, you can click on the job row to open the results page.
        
        From the results page you can download the model files in ZIP format to your working environment including structures and their associated confidence values:
        
        - Five .cif files named fold_<job_name>_model_<N>cif, where "<N>" is the rank of the predicted structure. Structures are ranked from 0 to 4, where 0 has the highest confidence. The .cif files contain predicted structures in the mmCIF format. They can be viewed in any molecular viewer like PyMOL or ChimeraX.
        - Five .json files named fold_<job_name>_summary_confidences_<N>.json, where "<N>" is the rank of the predicted structure from 0 to 4. These .json files contain summaries of the confidence metrics for the predictions (see below for more details on confidence metrics).
        - Five .json files named fold_<job_name>_full_data_<N>.json, where "<N>" is the rank of the predicted structure from 0 to 4. These .json files contain detailed confidence metrics, such as full PAE data, for the predictions (see below for more on confidence metrics).
        - A file named fold_<job_name>_job_request.json. This contains the inputs of the modelling job and could be used to re-run the job (for more details, see Advanced use of AlphaFold Server).
        - A file named terms_of_use.md. This is a legal document detailing the terms of use for the predictions. 

        Select the model_0 mmCIF file (`.cif`) to work with the model that has the highest confidence.
        
Next step is to compare the biophysical profiles of the wild vs variant sequences using the B2bTools to find differences. 

!!! example "Hands-on: Predicting the biophysical profiles"

    Manually "align" both sequences before submitting the "Multiple Sequence Alignment" analysis on the [B2BTools platform](https://bio2byte.be/online_predictors/). This MSA file can be named `P07949.mutation.msa.fasta`.

    ??? success "Solution"
    
    TBC


## 4.2 Combining PTM annotation to biophysical properties from B2Btools 
Here you can enter text and if you need to cite[@creative_commons_2022]

!!! example "Challenge 1"

    This is an example of text of Challenge 1

    ??? success "Solution"

        TBC


## 4.3 Coordinated 1D-2D-3D visualization of PTMs, mutations and biophysical properties


<div class="nightingale" style="width: 1500px;">
    <iframe src="/../assets/html/nightingale_pdbe_backbone_biophys_P07949.html" height="1768" width="2048" title="1D-2.5D-3D"></iframe>
</div>

_Representation 1D & 3D_

---

!!! note "To conclude: : Go to chapter 5"
    [Next chapter](/../../chapters/chapter_05) wraps up all the learnings and hands on activities.
