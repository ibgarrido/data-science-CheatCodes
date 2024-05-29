# Use the official Apache Spark base image
FROM bitnami/spark:latest

# Install Python and Jupyter
USER root
RUN apt-get update && apt-get install -y python3 python3-pip && \
    pip3 install --no-cache-dir notebook pyspark

# Set environment variables
ENV JAVA_HOME=/opt/bitnami/java
ENV SPARK_HOME=/opt/bitnami/spark
ENV PATH=$PATH:$SPARK_HOME/bin

# Expose ports for Jupyter Notebook and Spark UI
EXPOSE 8888 4040

# Create a working directory
RUN mkdir -p /opt/bitnami/spark/work-dir
WORKDIR /opt/bitnami/spark/work-dir

# Copy a Jupyter configuration file
COPY jupyter_notebook_config.py /root/.jupyter/

# Start Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root"]

