<template>
    <div class="row">
        <div class="col">
            <p>
            Last revision: 2022-08-18
            </p>
            <p style="font-weight: bold;">
                This is a tool for (slightly more) easily editing the DSS metadata. 
                Please note: By DSS we do in this context mean an advisory system with at least one (prediction) model 
                (what many might consider a DSS in itself). For example: VIPS is a DSS wich has pest prediction models 
                for Potato late blight, Carrot rust fly etc. This may differ from your understanding of what a DSS is. 
                In the IPM Decisions platform, the "DSS" (as used here) is called "Source", and each "model" as used here
                is called DSS.
            </p>
            <ol>
                <li>
                    <em>(If you have no previous data entered, skip to step 2)</em> To start editing, 
                    click the "Show YAML data" button. That opens up the text area where you can paste your current data.
                    Paste the data, and click "Load from YAML to form". The loading can take a few seconds, depending on
                    the complexity of the data.
                </li>
                <li>
                    Edit the data in the form ("The IPM Decisions DSS metadata schema" below) until it is correct
                </li>
                <li>
                    Click the "Load from form to YAML" button. The data from the form is now ready to be copied and pasted
                    into your YAML file. If you don't have this already, create a file named [YOUR_DSS_NAME].yaml
                </li>
            </ol>
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
                <li><span class="dssParamName">models[x].name</span> ("Model name")</li>
                <li><span class="dssParamName">models[x].id</span> ("The list of DSS models" -&gt; item x -&gt; "Model ID)")</li>
                <li><span class="dssParamName">models[x].purpose</span> ("The list of DSS models" -&gt; item x -&gt; "Purpose of the model")</li>
                <li><span class="dssParamName">models[x].description</span> ("The list of DSS models" -&gt; item x -&gt; "Description")</li>
                <li>(*) <span class="dssParamName">models[x].pests</span> ("The list of DSS models" -&gt; item x -&gt; "List of relevant pests (EPPO codes)")</li>
                <li>(*) <span class="dssParamName">models[x].crops</span> ("The list of DSS models" -&gt; item x -&gt; "List of relevant crops (EPPO codes)")</li>
                <li><span class="dssParamName">models[x].authors[x].name</span> ("The list of DSS models" -&gt; item x -&gt; "Author(s) of the model" -&gt; "Author name")</li>
                <li><span class="dssParamName">models[x].authors[x].organization</span> ("The list of DSS models" -&gt; item x -&gt; "Author(s) of the model" -&gt; "Author organization")</li>
                <li>(*) <span class="dssParamName">models[x].valid_spatial.countries</span> ("The list of DSS models" -&gt; item x -&gt; "List of countries (country codes)")</li>
                <li><span class="dssParamName">models[x].output.warning_status_interpretation</span> ("The list of DSS models" -&gt; item x -&gt; "Warning status interpretation")</li>
                
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
</template>