FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# Install Java 11 and Python 3.11 (plus minimal supporting tools).
RUN apt-get update && \
    # Bring in base packages and keep image lean by skipping extras.
    apt-get install -y --no-install-recommends \
        # Includes trusted root certificates for HTTPS connections.
        ca-certificates \
        # Provides curl for fetching remote content and scripts.
        curl \
        # Supplies GPG so we can verify repository signatures.
        gnupg \
        # Installs the full Java 11 Development Kit.
        openjdk-11-jdk \
        # Adds helpers for managing additional apt repositories.
        software-properties-common && \
    # Enable the deadsnakes PPA to access newer Python builds.
    add-apt-repository -y ppa:deadsnakes/ppa && \
    # Refresh package lists after adding the new repository.
    apt-get update && \
    # Install Python 3.11 plus its standard packaging utilities.
    apt-get install -y --no-install-recommends \
        # Core Python 3.11 interpreter.
        python3.11 \
        # Provides distutils module needed by some installers.
        python3.11-distutils \
        # Supplies venv module for creating virtual environments.
        python3.11-venv && \
    # Install or upgrade pip/setuptools for Python 3.11.
    python3.11 -m ensurepip --upgrade && \
    # Make python3 point to the 3.11 interpreter for convenience.
    ln -sf /usr/bin/python3.11 /usr/local/bin/python3 && \
    # Make python (no version) also point to Python 3.11.
    ln -sf /usr/bin/python3.11 /usr/local/bin/python && \
    # Clean up cached apt data to keep the image small.
    rm -rf /var/lib/apt/lists/*
