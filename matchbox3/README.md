# Matchbox

This setup contains an image of [MatchBox](https://github.com/ahdis/matchbox) along with a lightweight HTTP server and an application. The application is designed to facilitate the debugging of SDC data extraction from questionnaires.

## Running

By default, the hapi server is configured to run at [http://localhost:8080](http://localhost:8080) (server base endpoint at [http://localhost:8080/fhir](http://localhost:8080/fhir)) and the web server and application are accessible at [http://localhost:8083](http://localhost:8083).

## Configuration

The server's configuration can be manipulated via the `.env` file. If you need to modify the server port, you will need to update this in the `index.html` file of the app accordingly.

## App Functionality

The application queries the server for questionnaires and populates a dropdown menu with the titles of these questionnaires. When a user selects a questionnaire, the application sends a request to the server to retrieve the associated structure map - the association is done with the SDC extension ([http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-targetStructureMap](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-targetStructureMap)).

The app then presents the Questionnaire using LHC Forms, while also displaying the FML contained within the structure map. If the FML is edited, it can be POSTed back to the server and the `$extract` operation can be triggered using the Extract button.

This simple setup is intended to help iterating the FML editing for StructureMap extraction.
