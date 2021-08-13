<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <title>Grogle</title>
  <base href="/" />
</head>
<style type="text/css">
.liste{
    display: flex;
    height: 354px;
    flex-direction: column;
    overflow: auto;
    min-width: 372px;
}
body{
    font-size: small;
    font-weight: 700;
    color: royalblue;
    border-style: none;
    font-family: Arial, Helvetica, sans-serif;
}
.content{
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    width: 100%;
}
.column{
    padding-left: 16px;
    padding-right: 16px;
    width: 100%;
}
.brouillon{
    width: 90%;
    min-height: 354px;
}
.groupe-ville{
    display: flex;
    width: 100%;
    justify-content: space-between;
}
.groupe-input{
    width: 100%;
  
}
.textarea{
    font-size: medium;
    font-weight: 500;
    font-family: Arial, Helvetica, sans-serif;
}
input{
    margin: 2px;
    border: 1px solid #dfe1e5;
    border-radius: 8px;
    padding: 6px;
    font-size: small;
    font-weight: 500;
    text-transform: uppercase;
    width: -webkit-fill-available;
}
button{
    margin: 4px;
    min-height: 28px;
    border-radius: 8px;
    background-color: cornflowerblue;
    font-weight: 700;
    color: white;
    border-color: cornflowerblue;
    border-style: solid;
}
button:hover {
    box-shadow: rgb(0 0 0 / 30%) 2px 2px 4px;
}
.label{
    font-size: smaller;
}
.table-label{
    text-align: end;
    font-size: smaller;
}
.resultat-td{
    padding-top: 2rem;
    color: black;
}
.black{
    color: black;
}
.red{
    color: red;
}
.uppercase{
    text-transform: uppercase;
}
.card{
    box-shadow: rgb(0 0 0 / 12%) 0px 4px 16px;
    border: solid 1px cornflowerblue;
    border-radius: 8px;
    min-height: 354px;
    width: 100%;
    padding: 8px;
}
.item{
    display: flex;
    flex-direction: column;
    /* padding: 8px;
    border: solid 1px cornflowerblue;
    border-radius: 8px;
    box-shadow: rgb(0 0 0 / 12%) 0px 4px 16px; */
}
.table-fr{
    border: solid 1px red;
    border-radius: 4px;
    margin-top: 8px;
}
.table-sans{
    border: solid 1px cornflowerblue;
    border-radius: 4px;
    margin-top: 8px;
}
.inputfile {
	width: 0.1px;
	height: 0.1px;
	opacity: 0;
	overflow: hidden;
	position: absolute;
	z-index: -1;
}
.inputfile + label {
    margin: 4px;
    min-height: 28px;
    border-radius: 8px;
    background-color: cornflowerblue;
    font-weight: 700;
    color: white;
    border-color: cornflowerblue;
    border-style: solid;
    text-align: center;
    display: flex;
    padding: 4px;
    align-items: center;
}

.inputfile:focus + label,
.inputfile + label:hover {
    box-shadow: rgb(0 0 0 / 30%) 2px 2px 4px;
}
.search{
    font-size: larger;
    margin-left: 36px;
    border-color: cornflowerblue;
    border-radius: 24px;
}
.search:focus-visible {
    border-radius: 8px;
}
.search-label{
    font-size: large;
    font-weight: 700;
    color:royalblue;
}
.header{
    display: flex;
    flex-direction: column;
    font-size: medium;
    padding: 8px; 
    align-items: center;
}
</style>
<body onload="onload()">
    <div class="header">
        <label class="search-label" >Recherche Grogle</label>
        <div style="display: flex;width: 50%;">
            <input class="search" type="text" id="searchtext"><button id="btonEffacerSearch">Effacer</button>
        </div>
    
    </div>
    <div >
        <div class="content" >
            <div class="column">
                <div style="width: 100%;text-align: center;">
                    Note : 
                    <button id="btonEffacerNote">Effacer</button>
                </div>
                
                <textarea class="card textarea" id="note" class="brouillon" >
            
                </textarea>
            </div>
            <div class="column">
                <div style="width: 100%;text-align: center;">
                    Calcul : 
                    <button id="btonEffacerCalcul">Effacer</button>
                </div>
                <div class="card">
                    <table style="border-collapse: collapse;">
                        <tr>
                            <th></th>
                            <th>HT</th>
                            <th>TTC</th>
                        </tr>
                        <tr>
                            <td class="table-label">Montant Facture</td>
                            <td><input id="totalHT" class="line-calc" type="number" min="0"></td>
                            <td><input id="totalTTC" class="line-calc" type="number" min="0"></td>
                        </tr>
                        <tr>
                            <td class="table-label">Exclusion</td>
                            <td><input id="exclus1HT" class="line-calc" type="number" min="0"></td>
                            <td><input id="exclus1TTC" class="line-calc" type="number" min="0"></td>
                        </tr>
                        <tr>
                            <td class="table-label">Exclusion</td>
                            <td><input id="exclus2HT" class="line-calc" type="number" min="0"></td>
                            <td><input id="exclus2TTC" class="line-calc" type="number" min="0"></td>
                        </tr>
                    </table>
                    <table class="table-sans">
                     
                        <tr class="table-label">
                            <td class="black table-label uppercase">Total sans franchise</td>
                            <td class="resultat-td"><input id="resultatHT" value="0" type="number" min="0" disabled="true"></td>
                            <td class="resultat-td"><input id="resultatTTC" value="0" type="number" min="0" disabled="true"></td>
                        </tr>
                    </table>
                    <table class="table-fr">
                        <tr>
                            <td class="red table-label">Franchise</td>
                            <td ><input id="franchiseHT" class="line-calc" type="number" min="0" disabled="true"></td>
                            <td ><input id="franchiseTTC" class="line-calc" type="number" min="0" disabled="true"></td>
                        </tr>

                        <tr class="table-label">
                            <td class="red table-label uppercase">Total avec Franchise</td>
                            <td ><input id="finalHT" value="0" type="number" min="0" disabled="true"></td>
                            <td ><input id="finalTTC" value="0" type="number" min="0" disabled="true"></td>
                        </tr>
                      
                      </table>
                </div>
     
            </div>
            <div class="column">
                <div style="width: 100%;text-align: center;">
                    <button id="btonAjouter">Ajouter un nouvel élément</button>
                    <label id="infoLine" style="font-size: smaller;text-align: center;color: cornflowerblue;"></label>
                </div>
              
                <div id="elements" class="liste card">
                    
                </div>
                <script>
                    let searchText = '';
                    document.getElementById("btonEffacerNote")
                    .addEventListener("click", function() {
                        const note = document.getElementById("note")
                        note.value = "";
                  
                    });
                
                    document.getElementById("btonEffacerSearch")
                    .addEventListener("click", function() {
                        const note = document.getElementById("searchtext")
                        note.value = "";
                        searchText = "";
                        filterData();
                    });
                    document.getElementById("searchtext")
                    .addEventListener('input', function(event) {
                    searchText = event.target.value;
                    filterData();
                    });
                    function filterData(){
                        if ( searchText && searchText.length > 2 ){
                            selectData = filterArrayByString(originalData, searchText);
                        } else {
                            const itemData = originalData.find(_item => _item.nom === '');
                            selectData = [];
                            if (itemData){
                                selectData.push(itemData);
                            } 
                  
                        }
                        const infos = document.getElementById('infoLine');
                        if (selectData.length > 0){
                            infos.innerText = 'Nombre d\'éléments affichés : ' + selectData.length;
                        } else {
                            infos.innerText = "0";
                        }
                        infos.innerText += ' / ' + originalData.length;
                      
                        let elt = document.getElementById('elements');
                            while (elt.firstChild) {
                                 elt.removeChild(elt.firstChild);
                            }
                    
                        selectData.forEach((element, index) => {
                            const item = document.createElement("div");
                            item.classList.add('item');

                            item.appendChild(setGroup('nom','Nom : ', element.nom));
                            item.appendChild(setGroup('adresse','Adresse : ', element.adresse));
                            const groupe = document.createElement("div");
                            groupe.appendChild(setGroup('codepostal','Code Postal : ', element.codepostal));
                            groupe.appendChild(setGroup('ville','Ville : ', element.ville));
                            groupe.classList.add("groupe-ville");
                            item.appendChild(groupe);
                            item.appendChild(setGroup('email','Email : ', element.email));
                            item.appendChild(setGroup('telephone','Telephone : ', element.telephone));
                            item.appendChild(setGroup('note','Note : ', element.note));
                            const bton = document.createElement("button");
                            bton.value = "Modifier"
                            bton.innerText = "Modifier"
                            bton.addEventListener('click', function(){
                                element.nom = document.getElementsByClassName('nom')[index].value;
                                element.adresse = document.getElementsByClassName('adresse')[index].value;
                                element.ville = document.getElementsByClassName('ville')[index].value;
                                element.codepostal = document.getElementsByClassName('codepostal')[index].value;
                                element.email = document.getElementsByClassName('email')[index].value;
                                element.telephone = document.getElementsByClassName('telephone')[index].value;
                                element.note = document.getElementsByClassName('note')[index].value;
                                filterData();
                            });
                            
                            item.appendChild(bton);
                            elt.appendChild(item);
                        });
                    }
          
                    function setGroup(classe, name, value){
                        const groupe = document.createElement("div");
                        groupe.classList.add("groupe-input")
                        const label = document.createElement("label");
                        label.innerText = name;
                        label.classList.add('label');
                        groupe.appendChild(label);
                        const nom = document.createElement("input");
                            nom.classList.add(classe);
                            nom.value = value;
                        groupe.appendChild(nom);
                        return groupe;
                    }
                </script>
            </div>

        </div>
        <div style="display: flex;">
            <button onclick="export2txt()">Exporter les données dans un fichier</button>
            <input type="file" name="inputfile"
            class="inputfile"
            accept=".grogle"
            id="inputfile">
            <label for="inputfile">Ouvrir un fichier grogle</label>
            <button onclick="keySend()">test</button>
        </div>
  
    </div>

<script>
    function onload(){
        console.log('onload');
        // const input  = document.getElementById('inputfile');
        // input.click();
    }
    // TABLE DE CALCUL
    document.getElementById("btonEffacerCalcul")
                    .addEventListener("click", function() {
                        const totalHT = document.getElementById("totalHT")
                        totalHT.value = "0.00";
                        const totalTTC = document.getElementById("totalTTC")
                        totalTTC.value = "0.00";
                        const exclus1H = document.getElementById("exclus1HT")
                        exclus1H.value = "0.00";
                        const exclus2H = document.getElementById("exclus2HT")
                        exclus1H.value = "0.00";
                        const exclus1T = document.getElementById("exclus1TTC")
                        exclus1T.value = "0.00";
                        const exclus2T = document.getElementById("exclus2TTC")
                        exclus2T.value = "0.00";
                        updateResultat();
                    });
    document.getElementById('totalHT')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ht = value.target.value;
        const ttc = Math.round(ht * 1.2 * 100) / 100;
        const txtTTC = document.getElementById("totalTTC")
        txtTTC.value = ttc.toFixed(2);
        updateResultat();
    });
    document.getElementById('totalTTC')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ttc = value.target.value;
        const ht = Math.round(ttc / 1.2 * 100) / 100;
        const txtHT = document.getElementById("totalHT")
        txtHT.value = ht.toFixed(2);
        updateResultat();
    });
    document.getElementById('exclus1HT')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ht = value.target.value;
        const ttc = Math.round(ht * 1.2 * 100) / 100;
        const txtTTC = document.getElementById("exclus1TTC")
        txtTTC.value = ttc.toFixed(2);
        updateResultat();
    });
    document.getElementById('exclus1TTC')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ttc = value.target.value;
        const ht = Math.round(ttc / 1.2 * 100) / 100;
        const txtHT = document.getElementById("exclus1HT")
        txtHT.value = ht.toFixed(2);
        updateResultat();
    });
    document.getElementById('exclus2HT')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ht = value.target.value;
        const ttc = Math.round(ht * 1.2 * 100) / 100;
        const txtTTC = document.getElementById("exclus2TTC")
        txtTTC.value = ttc.toFixed(2);
        updateResultat();
    });
    document.getElementById('exclus2TTC')
    .addEventListener('change', (value)=> {
        console.log('totalHT Value', value);
        const ttc = value.target.value;
        const ht = Math.round(ttc / 1.2 * 100) / 100;
        const txtHT = document.getElementById("exclus2HT")
        txtHT.value = ht.toFixed(2);
        updateResultat();
    });
    function updateResultat(){
        console.log('updateResultat');
        const txtHT = document.getElementById("totalHT");
        const txtTTC = document.getElementById("totalTTC");
        let resultatHT = document.getElementById("resultatHT");
        let resultatTTC = document.getElementById("resultatTTC");
        const txtExclus1HT = document.getElementById("exclus1HT");
        const txtExclus2HT = document.getElementById("exclus2HT");
        const txtExclus1TTC = document.getElementById("exclus1TTC");
        const txtExclus2TTC = document.getElementById("exclus2TTC");
        let franchiseHT = document.getElementById("franchiseHT");
        let franchiseTTC = document.getElementById("franchiseTTC");
        let finalHT = document.getElementById("finalHT");
        let finalTTC = document.getElementById("finalTTC");
        let ht = txtHT.value;

        ht -= txtExclus1HT.value;
        ht -= txtExclus2HT.value;
        ht = Math.round(ht * 100) / 100;
        console.log('updateResultat HT', ht);
        resultatHT.value = ht.toFixed(2);
        let ttc = ht * 1.2;
        ttc = Math.round(ttc * 100) / 100;
        resultatTTC.value = ttc.toFixed(2);

        let frHT = (ht * 20) / 100;
        console.log('frHT', frHT);
        if ( frHT < 15){ frHT = 15; }
        if (frHT > 75){ frHT = 75; }
        frHT = Math.round(frHT * 100) / 100;
        franchiseHT.value = frHT.toFixed(2);

        let frTTC = (ttc * 20) / 100;
        if ( frTTC < 15){ frTTC = 15; }
        if (frTTC > 75){ frTTC = 75; }
        frTTC = Math.round(frTTC * 100) / 100;
        franchiseTTC.value = frTTC.toFixed(2);

        ht -= frHT;
        ttc -= frTTC;
        finalHT.value = ht.toFixed(2);
        finalTTC.value = ttc.toFixed(2);


    }

    // 
    function keySend(){
        console.log('keysend');
        setTimeout(function(){    
            console.log('timeout');
            window.dispatchEvent(new KeyboardEvent('keydown', {
  'key': 'a'
})); }, 3000);
     
    }

    document.getElementById('btonAjouter')
    .addEventListener('click', function(){
        const newData = {
        nom: "",
        adresse: "",
        codepostal: "",
        ville: "",
        email: "",
        telephone: "",
        note: ""
      }
      originalData.push(newData);
      searchText = '';
      filterData();
    });
       document.getElementById('inputfile')
       .addEventListener('change', function(event) {
            const files = event.srcElement.files;
                       var fr = new FileReader();
                       fr.onload = function(){
                        originalData = JSON.parse(fr.result);
                        filterData();
                       }
                       fr.readAsText(files[0]);
                   })
    let pathFolder = "%user/";
    function getEnv(){
    }
    let selectData = [];
    let originalData = []
  ;
  function readFile(file) {
  return new Promise((resolve, reject) => {
    let fr = new FileReader();
    fr.onload = x=> resolve(fr.result);
  reader.onload = function(e) {
    document.getElementById('contents').innerHTML = e.target.result;
  }
  reader.readAsText(file)
})}

function export2txt() {
  const a = document.createElement("a");
  const fileData = JSON.stringify(originalData);
  a.href = URL.createObjectURL(new Blob([fileData], {
    type: "text/html"
  }));
  let path = window.location.pathname;
  path = 'data.grogle';
    a.setAttribute("download", path);
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
}

function filterArrayByString(mainArr, searchText)
    {
        if ( searchText === '' )
        {
            return mainArr;
        }

        searchText = searchText.toLowerCase();

        return mainArr.filter(itemObj => {
            return searchInObj(itemObj, searchText);
        });
    }
function searchInArray(arr, searchText)
    {
        for ( const value of arr )
        {
            if ( typeof value === 'string' )
            {
                if ( searchInString(value, searchText) )
                {
                    return true;
                }
            }

            if ( typeof value === 'object' )
            {
                if ( searchInObj(value, searchText) )
                {
                    return true;
                }
            }
        }
    }
    function searchInString(value, searchText)
    {
        return value.toLowerCase().includes(searchText);
    }
    function searchInObj(itemObj, searchText)
    {
        for ( const prop in itemObj )
        {
            if ( !itemObj.hasOwnProperty(prop) )
            {
                continue;
            }

            const value = itemObj[prop];
            if ( typeof value === 'string' )
            {
                if ( searchInString(value, searchText) )
                {
                    return true;
                }
            }

            else if ( Array.isArray(value) )
            {
                if ( searchInArray(value, searchText) )
                {
                    return true;
                }
            }

            if ( typeof value === 'object' )
            {
                if ( searchInObj(value, searchText) )
                {
                    return true;
                }
            }
        }
    }

</script>
<footer>

</footer>
</body>

</html>
