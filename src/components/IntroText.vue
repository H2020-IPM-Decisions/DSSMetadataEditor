<script setup>
    import screenshotPDFUrl from "../assets/documents/platform_screenshots.pdf"
</script>
<style>
  .infoBox {
    border: 1px solid black; 
    padding: 15px 15px 15px 35px; 
    margin-bottom: 15px; 
    background-color: #eeeeee; 
    border-radius: .25em;
  }

</style>
<template>
    <div class="row">
        <div class="col">
            <p>
            Last revision: 2022-10-12
            </p>
            <p style="font-weight: bold;">
                This is a tool for quick editing of the Decision Support System (DSS) metadata. 
                Please note: Here "DSS" means an an advisory system with one or more prediction models. For example: 
                <a href="https://www.vips-landbruk.no/" target="new">VIPS</a> is a DSS which has pest prediction models 
                for several pests (e.g. <a href="https://www.vips-landbruk.no/forecasts/models/NEGPROGMOD/" target="new">Potato late blight</a>, 
                <a href="https://www.vips-landbruk.no/forecasts/models/PSILARTEMP/" target="new">Carrot rust fly</a> etc.).
                In the IPM Decisions platform, the "DSS" (as used here) is called "Source", and each "model" as used here
                is called DSS.
            </p>
            <div class="infoBox">
                <h2>Steps to complete the editing of the file</h2>
                <p><em style="font-weight:bold;">If this is the first time you are creating IPM Decisions metadata for a DSS, skip to step 2.</em></p>
                <h3>Step 1 - Import data from existing metadata file (YAML format)</h3>
                <p>
                    To start editing an existing metadata file, click the "Show YAML data" button in the "Converting data between form and YAML" box. 
                    This opens up a text area where you can paste your current data.
                    Your current data would come from a pure text file whose name ends with ".yaml". Use e.g. Notepad to open it,
                    copy the data from the file, paste it into the text area and click "Load from YAML to form". 
                    The loading can take a few seconds, depending on the complexity of the data, and will auto-fill "The IPM Decisions DSS 
                    metadata schema" below. If you have no previous data entered, skip to step 2.
                </p>
                <h3>Step 2 - Enter data in the proforma (New DSSs start here)</h3>
                <p>
                    Fill/edit the data in "The IPM Decisions DSS metadata schema" below until it is correct. Expand the "Help/documentation" section below 
                    for detailed instructions.
                </p>
                <h3>Step 3 - Export data from proforma to YAML file</h3>
                <p>
                    Return to the "Converting data between form and YAML" box, and click the "Load from form to YAML" button. The 
                    text area (visible when you click the "Show YAML data" button) above the form
                    is then filled with the YAML(text) representation of the data. This is what the DSS API requires to run your model(s) 
                    internally. These text data must be copied from the text field and pasted into a YAML file, which is a pure text file 
                    that has a filename that ends with ".yaml", ideally named [YOUR_DSS_NAME].yaml, for instance "dk.seges.yaml". If you don't have this already, create a file named [YOUR_DSS_NAME].yaml. This can be
                    done in any simple text editor like e.g. Notepad. <em>Please note that you cannot use advanced word processors like Word 
                        or LibreOffice Write, since they add formatting codes behind the scenes that are invisible to the user, but makes the file
                    unparseable by the application.</em>
                </p>
                <h3>Step 4</h3>
                <p>
                    Send this file to your IPM Decisions technical contact.
                </p>
                
            </div>
            <h2>Help/documentation 
                <input type="checkbox" class="btn-check" id="btn-check" autocomplete="off">
                <label class="btn btn-primary" for="btn-check" onclick="this.innerHTML=this.innerHTML == ('+') ? '-':'+'; document.getElementById('help').style.display=this.innerHTML == ('+') ? 'none':'block';">+</label>
            </h2>
            <div id="help" class="infoBox" style="display:none;">
                <h3>Searching in the proforma</h3>
                <p>To search in the proforma, use the browser's search function. In most browsers you can activate it by typing CTRL-F. Below is a screenshot from Firefox.</p>
                <p><img src="@/assets/images/metadata_help_0.png" style="border: 4px solid white;"/></p>
                <h3>Fields visible to the user</h3>
                <p>
                Fields that are visible to users in the platform are labeled with reference [#] to <a :href="screenshotPDFUrl" target="new">this document</a>, 
                with screen shots with corresponding labels. For instance, this field (below)
                </p>
                <p><img src="@/assets/images/metadata_help_1.png"/></p>
                <p>...is shown on the platform as illustrated in the document screenshot below</p>
                <p><img src="@/assets/images/metadata_help_2.png"/></p>
                <h4>Index of user visible parameters</h4>
                <p>Parameters marked (*) appear to the user, but transformed from codes to user known entities (e.g. not EPPO codes, but species names)</p>
                <ol>
                    <li><span class="dssParamName">name</span> ("DSS name")</li>
                    <li><span class="dssParamName">organization.name</span> ("Organization name")</li>
                    <li><span class="dssParamName">organization.country</span> ("Organization country")</li>
                    <li><span class="dssParamName">models[].name</span> ("Model name")</li>
                    <li><span class="dssParamName">models[].id</span> ("The list of DSS models" -&gt; "Model ID)")</li>
                    <li><span class="dssParamName">models[].purpose</span> ("The list of DSS models" -&gt;  "Purpose of the model")</li>
                    <li><span class="dssParamName">models[].description</span> ("The list of DSS models" -&gt; "Description")</li>
                    <li>(*) <span class="dssParamName">models[].pests</span> ("The list of DSS models" -&gt; "List of relevant pests (EPPO codes)")</li>
                    <li>(*) <span class="dssParamName">models[].crops</span> ("The list of DSS models" -&gt; "List of relevant crops (EPPO codes)")</li>
                    <li><span class="dssParamName">models[].authors[].name</span> ("The list of DSS models" -&gt; "Author(s) of the model" -&gt; "Author name")</li>
                    <li><span class="dssParamName">models[].authors[].organization</span> ("The list of DSS models" -&gt; "Author(s) of the model" -&gt; "Author organization")</li>
                    <li>(*) <span class="dssParamName">models[].valid_spatial.countries</span> ("The list of DSS models" -&gt; "List of countries (country codes)")</li>
                    <li><span class="dssParamName">models[].output.warning_status_interpretation</span> ("The list of DSS models" -&gt; "Warning status interpretation")</li>
                </ol>
                <h4>DSS Metadata for external link DSS</h4>
                <p>
                    The external link DSS do not need as much information as the integrated DSS, since they do not take inputs or require weather data. 
                    External link DSSs should enter this information (if applicable):
                </p>
                <ul>
                    <li>DSS id</li>
                    <li>DSS version</li>
                    <li>DSS name</li>
                    <li>DSS web address</li>
                    <li>DSS organization info</li>
                    <li>Supported languages</li>
                    <li>
                        For each model:
                        <ul>
                            <li>Model name</li>
                            <li>Model ID</li>
                            <li>Model version</li>
                            <li>Type of decision</li>
                            <li>Type of output</li>
                            <li>Description URL</li>
                            <li>Purpose of the model</li>
                            <li>Description</li>
                            <li>Citations</li>
                            <li>Keywords</li>
                            <li>List of relevant crops</li>
                            <li>Author(s) of the model</li>
                            <li>Type of execution -- Set this to "LINK"</li>
                            <li>Spatial (geographic) validity</li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>