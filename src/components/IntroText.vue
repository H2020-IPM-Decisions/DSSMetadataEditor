<template>
    <div class="row">
        <div class="col">
            This is a tool for (slightly more) easily editing the DSS metadata. 
            <ol>
                <li>
                    (If you have no previous data entered, skip this step) To start editing, 
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
        </div>
    </div>
</template>