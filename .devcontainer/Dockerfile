FROM rocker/geospatial:4.4

# Install Python 3.12 (Ubuntu 24.04 Noble default)
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-dev \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Install additional R packages
# (tidyverse, sf, and all geospatial system libs are pre-installed in rocker/geospatial)
COPY setup.R /tmp/setup.R
RUN Rscript /tmp/setup.R

# Install Python dependencies
# --break-system-packages required on Ubuntu 24.04 (PEP 668)
COPY requirements.txt /tmp/requirements.txt
RUN pip3 install --break-system-packages -r /tmp/requirements.txt
