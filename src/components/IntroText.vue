<template>
    <div class="row">
        <div class="col">
            <p>
            This is a tool for (slightly more) easily editing the DSS metadata. 
            </p>
            <ol>
                <li>
                    <em>(If you have no previous data entered, skip this step)</em> To start editing, 
                    click the "Show YAML data" button. That opens up the text area where you can paste your current data.
                    Paste the data, and click "Load from YAML to form". The loading can take a few seconds, depending on
                    the complexity of the data.
                </li>
                <li>
                    Edit the data in the form until it is correct
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
                <li>name</li>
                <li>organization.name</li>
                <li>organization.country</li>
                <li>models[x].name</li>
                <li>models[x].id</li>
                <li>models[x].purpose</li>
                <li>models[x].description</li>
                <li>models[x].pests*</li>
                <li>models[x].crops*</li>
                <li>models[x].authors[x].name</li>
                <li>models[x].authors[x].organization</li>
                <li>models[x].valid_spatial.countries*</li>
                <li>models[x].output.warning_status_interpretation</li>
                
            </ol>
        </div>
    </div>
</template>