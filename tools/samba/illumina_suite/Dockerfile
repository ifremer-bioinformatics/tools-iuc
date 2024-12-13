# Use the specified base image from Quay.io
FROM quay.io/qiime2/amplicon:2024.10

# Install necessary tools for cloning and building
RUN apt-get update && apt-get install -y \
    git \
    python3-dev \
    build-essential \
    && apt-get clean

# Clone the q2-dbotu repository and install it
RUN git clone https://github.com/cduvallet/q2-dbotu.git /tmp/q2-dbotu && \
    cd /tmp/q2-dbotu && \
    python3 setup.py install && \
    cd / && \
    rm -rf /tmp/q2-dbotu  # Clean up temporary files

# Create input and output directories with proper permissions
RUN mkdir -p /input /output \
    && chmod 777 /input /output

# Set the working directory to /input
WORKDIR /input

# Default command to keep the container running or to execute a shell
CMD ["bash"]
