<template>
    <div class="row">
        <div class="col">
            <p>
            Last revision: 2022-08-19
            </p>
            <p style="font-weight: bold;">
                This is a tool for quick editing of the Decision Support System (DSS) metadata. 
                Please note: Here "DSS" means an an advisory system with one or more prediction models. For example: 
                VIPS (https://www.vips-landbruk.no/) is a DSS wich has pest prediction models 
                for several pests (e.g. Potato late blight, Carrot rust fly etc.).
                In the IPM Decisions platform, the "DSS" (as used here) is called "Source", and each "model" as used here
                is called DSS.
            </p>
            <div style="border: 1px solid black; padding: 15px 15px 15px 35px; margin-bottom: 15px; background-color: #dddddd;">
                <h2>Steps to complete the editing of the file</h2>
                <ol >
                    <li>
                        <em style="font-weight:bold;">(If you have no previous data entered, skip to step 2)</em> To start editing, 
                        click the "Show YAML data" button. This opens up the text area where you can paste your current data.
                        Your current data would come from a pure text file whose name ends with ".yaml". Use e.g. Notepad to open it,
                        copy the data from the file, paste it into the text area and click "Load from YAML to form". 
                        The loading can take a few seconds, depending on the complexity of the data.
                    </li>
                    <li>
                        Edit the data in the form ("The IPM Decisions DSS metadata schema" below) until it is correct. See the "Help/documentation" section below 
                        for how to do that.
                    </li>
                    <li>
                        Click the "Load from form to YAML" button. The text area (visible when you click the "Show YAML data" button) above the form
                        is then filled with the YAML(text) representation of the data. This is what the DSS API uses internally. These text data 
                        must be copied from the text field and pasted into a YAML file, which is a pure text file that has a filename that ends with ".yaml",
                        ideally [YOUR_DSS_NAME].yaml, for instance "dk.seges.yaml". If you don't have this already, create a file named [YOUR_DSS_NAME].yaml. This can be
                        done in any simple text editor like e.g. Notepad.
                    </li>
                    <li>
                        Send this file to your IPM Decisions technical contact.
                    </li>
                </ol>
            </div>
            <h2>Help/documentation 
                <input type="checkbox" class="btn-check" id="btn-check" autocomplete="off">
                <label class="btn btn-primary" for="btn-check" onclick="this.innerHTML=this.innerHTML == ('+') ? '-':'+'; document.getElementById('help').style.display=this.innerHTML == ('+') ? 'none':'block';">+</label>
            </h2>
            <div id="help" style="display: none;">
                <p>
                Fields that are visible to users in the platform are labeled with reference [#] to other documentation 
                (<strong>TODO</strong>) with screen shots with corresponding labels.
                </p>
                <h4>Index of user visible parameters</h4>
                <p>Parameters marked (*) appear to the user, but in a translated form (e.g. not EPPO codes, but species names)</p>
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
                            <li style="font-weight: bold;">List of relevant pests(Not in Daves list)??</li>
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