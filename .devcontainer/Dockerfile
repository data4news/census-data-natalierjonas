FROM mcr.microsoft.com/devcontainers/python:1-3.11-bullseye

# Install R and system libraries required by geospatial R packages (sf, tidycensus, tigris)
RUN apt-get update && apt-get install -y --no-install-recommends \
    r-base \
    r-base-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    libfreetype6-dev \
    libpng-dev \
    libtiff5-dev \
    libjpeg-dev \
    libgdal-dev \
    libproj-dev \
    libgeos-dev \
    libudunits2-dev \
    && rm -rf /var/lib/apt/lists/*

# Install R packages — baked into the image so Codespaces loads instantly
COPY setup.R /tmp/setup.R
RUN Rscript /tmp/setup.R

# Install Python dependencies
COPY requirements.txt /tmp/requirements.txt
RUN pip install --upgrade pip && pip install -r /tmp/requirements.txt
