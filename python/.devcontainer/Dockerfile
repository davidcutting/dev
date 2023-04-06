FROM base-dev as python-dev

# Install base python development packages
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip

# Install Python build tools
RUN pip install poetry
