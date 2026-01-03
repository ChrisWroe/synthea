
# Generate patients with R4 FHIR output
./run_synthea -p 1000 --exporter.fhir.export=true --exporter.fhir.bulk_data=true

# Copy to GCP storage bucket
gcloud storage cp output/fhir/* gs://synthea_fhir_r4_1000_sample/synthea-data


gcloud healthcare fhir-stores import gcs FHIR_sample_store   --dataset=Synthetic_data_samples   --location=europe-west2   --gcs-uri=gs://synthea_fhir_r4_1000_sample/synthea-data/*.ndjson --project <GCP-PROJECT-NAME>