## Moving Your Docker Image to Google Cloud Artifact Registry

This guide walks you through pulling a Docker image from Docker Hub and pushing it to Google Cloud Artifact Registry (ACR) for secure and managed storage within your GCP project.

**Prerequisites:**

* A Docker Hub account with the desired image (replace `togo407/website:latest` with the actual image name and tag).
* A Google Cloud project with Artifact Registry enabled (see [https://cloud.google.com/artifact-registry](https://cloud.google.com/artifact-registry) for setup instructions).

**Steps:**

1. **Authenticate Docker with GCP:**

   ```bash
   gcloud auth configure-docker us-central1-docker.pkg.dev
   ```

   This command configures the Docker CLI to use your Google Cloud credentials when interacting with Artifact Registry. Replace `us-central1-docker.pkg.dev` with the appropriate region for your registry (see [https://cloud.google.com/artifact-registry/docs/repositories/repo-locations](https://cloud.google.com/artifact-registry/docs/repositories/repo-locations) for details).

2. **Pull the Image from Docker Hub:**

   ```bash
   docker pull togo407/website:latest
   ```

   This command pulls the specified image (`togo407/website:latest`) from Docker Hub and stores it locally on your system.

3. **Tag the Image for ACR:**

   ```bash
   docker tag docker.io/togo407/website:latest \
             us-central1-docker.pkg.dev/cloud-tutorial-435009/quickstart-docker-repo/togo407/website:latest
   ```

   This command creates a new tag for the image, specifying your Artifact Registry repository details:
      * `us-central1-docker.pkg.dev`: Replace with your region's Artifact Registry URL.
      * `cloud-tutorial-435009`: Replace with your project ID.
      * `quickstart-docker-repo`: Replace with the desired repository name in your project.

4. **Push the Image to ACR:**

   ```bash
   docker push us-central1-docker.pkg.dev/cloud-tutorial-435009/quickstart-docker-repo/togo407/website:latest
   ```

   This command pushes the newly tagged image to your Artifact Registry repository.

