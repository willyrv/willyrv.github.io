---
layout: post
title: Willy's PhD Defense
permalink: /phd_defense/
---


<script type="text/javascript">
function hideStuff(id) {
    // hide the element
    document.getElementById(id).style.display = 'none';
    
}

function showStuff(id) {
    // show the lorem ipsum text
    document.getElementById(id).style.display = 'block';
    
}
 
</script>


<script type="text/javascript">
    // Initialize Variables
    var closePopup = document.getElementById("popupclose");
    var overlay = document.getElementById("overlay");
    var popup = document.getElementById("popup");
    var button = document.getElementById("button");
    // Close Popup Event
    closePopup.onclick = function() {
        overlay.style.display = 'none';
        popup.style.display = 'none';
    };
    // Show Overlay and Popup
    function showPopup(id1, id2){
	document.getElementById(id1).style.display = 'block';
	document.getElementById(id2).style.display = 'block';
    }
    function hidePopup(id1, id2){
	document.getElementById(id1).style.display = 'none';
	document.getElementById(id2).style.display = 'none';
    }
</script>

<style>

.tableheader{
  background: #D5D5D5;
  height: 70px;
  font-size: 30px;
}

.tablerow{
  background: #FAFAFA;
  height: 70px;
}

.timedetails{
  width: 180px;
  text-align: center;
}



#overlay {
    display: none;
    position: absolute;
    top: 0;
    bottom: 0;
    background: #999;
    width: 100%;
    height: 100%;
    opacity: 0.8;
    z-index: 100;
}
.popup {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    background: #D3EFED;
    margin-left: -400px; /*Half the value of width to center div*/
    margin-top: -250px; /*Half the value of height to center div*/
    z-index: 200;
}
.popupclose {
    float: right;
    padding: 10px;
    cursor: pointer;
}
.popupcontent {
    padding: 10px;
    width: 700px;
    height: 400px;
    overflow-y: auto;
}
.popupcontrols{
    height: 30px;
    background: #8BBCCF;
}
#button {
    cursor: pointer;
}

</style>

<b>Date:</b> Monday, June 20, 2016. <br/>
<b>Place:</b> INSA-Toulouse.

<table id="schedule" style="border-collapse: collapse;">
   <thead>
      <tr class="tableheader">
         <th colspan="2">Programme</th>
      </tr>
   </thead>
   <tbody>
      <tr class="tablerow">
         <td class="timedetails">08:30 - 09:00</td>
         <td>WELCOME COFFEE</td>
      </tr>
      <tr class="tablerow">
         <td class="timedetails">09:00 - 09:45</td>
         <td>TALK 1 - <u>Rasmus Heller</u>. <i>Should we do genotyping by sequencing?</i>  <br> <span onclick="showPopup('popupRasmus', 'popupcloseRasmus'); return false;" style="cursor: pointer;">(view abstract)</span>
         <div id="popupRasmus" class="popup">
    <div class="popupcontrols">
        <span id="popupcloseRasmus" onclick="hidePopup('popupRasmus', 'popupcloseRasmus'); return false;" class="popupclose">x</span>
    </div>
    <div class="popupcontent">
        Genotyping by sequencing is becoming increasingly popular as a means of generating population and genomic scale data for non-model organisms. We used a small RADseq data set to examine potential problems or biases in common bioinformatics pipelines, using the site frequency spectrum as an informative summary of the data. We found that a standard RADseq genotyping tool overcalls singletons severely. This can be improved by eschewing genotype calls and using the genotype likelihood directly to infer the SFS. However, even after this the SFS from RADseq data is not identical to one obtained using whole-genome shotgun sequencing on the same individuals. Part of the explanation appears to be that the RADseq protocol produces a non-random subset of the genome which may have a different SFS form the genome-wide one. I discuss some implications of this and ongoing work on the topic.
    </div>
    </div>
         </td>
      </tr>
    <tr class="tablerow">
       <td class="timedetails">09:50 - 10:35</td>
       <td>TALK 2 - <u>Olivier François</u>. <i>Fast inference of individual ancestry coefficients using geographic data</i>. <span onclick="showPopup('popupOFrancois', 'popupcloseOFrancois'); return false;" style="cursor: pointer;">(view abstract)</span>
         <div id="popupOFrancois" class="popup">
    <div class="popupcontrols">
        <span id="popupcloseOFrancois" onclick="hidePopup('popupOFrancois', 'popupcloseOFrancois'); return false;" class="popupclose">x</span>
    </div>
    <div class="popupcontent">
        Geography and landscape are important determinants of genetic variation in natural populations, and several ancestry estimation methods have been proposed to investigate population structure using genetic and geographic data simultaneously. Those approaches are often based on computer-intensive stochastic simulations and do not scale with the dimensions of the data sets generated by high-throughput sequencing technologies. There is a growing demand for faster algorithms able to analyse genomewide patterns of population genetic variation in their geographic context. Here, we present TESS3, a major update of the spatial ancestry estimation program TESS. By combining matrix factorization and spatial statistical methods, TESS3 provides estimates of ancestry coefficients with accuracy comparable to TESS and with run-times much faster than the Bayesian version. In addition, the TESS3 program can be used to perform genome scans for selection, and separate adaptive from nonadaptive genetic variation using ancestral allele frequency differentiation tests. The main features of TESS3 are illustrated using simulated data and analysing genomic data from European lines of the plant species Arabidopsis thaliana.
    </div>
    </div>
      </td>
    </tr>
      <tr class="tablerow">
         <td class="timedetails">10:40 - 11:00</td>
         <td> COFFEE BREAK
         </td>
      </tr>
      <tr class="tablerow">
         <td class="timedetails">11:00 - 11:45</td>
         <td>TALK 3 - <u>Mark Beaumont</u>. <i>Expectation Propagation for demographic inference using genome data</i>. <span onclick="showPopup1('popupBeaumont', 'popupcloseBeaumont'); return false;" style="cursor: pointer;">(view abstract)</span>
         <div id="popupBeaumont" class="popup">
    <div class="popupcontrols">
        <span id="popupcloseBeaumont" onclick="hidePopup('popupBeaumont', 'popupcloseBeaumont'); return false;" class="popupclose">x</span>
    </div>
    <div class="popupcontent">
        
    </div>
    </div>
</td>
      </tr>    
      <tr class="tablerow">
         <td class="timedetails">11:50 - 13:30</td>
         <td> LUNCH TIME
         </td>
      </tr>
      <tr class="tablerow">
         <td class="timedetails">14:00 </td>
         <td>PhD DEFENSE - <u>Willy Rodriguez</u>. <i>Reconstructing the demographic history of populations from genomic data</i>. <span onclick="showPopup('popupWilly', 'popupcloseWilly'); return false;" style="cursor: pointer;">(view abstract)</span>
         <div id="popupWilly" class="popup">
    <div class="popupcontrols">
        <span id="popupcloseWilly" onclick="hidePopup('popupWilly', 'popupcloseWilly'); return false;" class="popupclose">x</span>
    </div>
    <div class="popupcontent">
    <p>
        The rapid development of DNA sequencing technologies is expanding the horizons of population genetic studies. It is expected that genomic data will increase our ability to reconstruct the history of populations. While this increase in genetic information will likely help biologists and anthropologists to reconstruct the demographic history of populations, it also poses big challenges. In some cases, simplicity of the model may lead to erroneous conclusions about the population under study. Recent works have shown that DNA patterns expected in individuals coming from structured populations correspond with those of unstructured populations with changes in size through time. As a consequence it is often difficult to determine whether demographic events such as expansions or contractions (bottlenecks) inferred from genetic data are real or due to the fact that populations are structured in nature. Moreover, almost no inferential method allowing to reconstruct past demographic size changes takes into account structure effects. </p>
        
	<p>In this thesis, some recent results in population genetics are presented: (i) a model choice procedure is proposed to distinguish one simple scenario of population size change from one of structured population, based on the coalescence times of two genes, showing that for these simple cases, it is possible to distinguish both models using genetic information form one single individual; (ii) by using the notion of instantaneous coalescent rate, it is demonstrated that for any scenario of structured population or any other one, regardless how complex it could be, there always exists a panmitic scenario with a precise function of population size changes having exactly the same distribution for the coalescence times of two genes. This not only explains why spurious signals of bottlenecks can be found in structured populations but also predicts the demographic history that actual inference methods are likely to reconstruct when applied to non panmitic populations. Finally, (iii) a method based on a Markov process is developed for inferring past demographic events taking the structure into account. This is method uses the distribution of coalescence times of two genes to detect past demographic changes in structured populations from the DNA of one single individual. Some applications of the model to genomic data are discussed.</p>
    </div>
    </div>
     </td>
      </tr>
      <tr class="tablerow">
         <td class="timedetails"></td>
         <td>BUFFET AND DRINKS (POT DE THESE)
         </td>
      </tr>
   </tbody>
</table>

<br>
<br>

<table style="border-collapse: collapse;">
   <thead>
      <tr class="tableheader">
         <th colspan="2"> Venue</th>
      </tr>
   </thead>
   <tbody>
   <tr class="tablerow">
         <td colspan="2"> To come to the INSA, take the subway (line B) in direction to "Ramonville" and get off at the station "Faculté de Pharmacie". The talks in the morning will take place in the GMM ("Génie Mathématique et Modélisation") building, room 139 (first floor). The PhD defense in the afternoon will take place in "Amphithéâtre Joseph Fourier". See the map <a href="https://drive.google.com/open?id=1DH6ifyOpMuI8xShMtyhKg2Zh210&usp=sharing">here</a>.
         </td>
      </tr>
   </tbody>
</table>


