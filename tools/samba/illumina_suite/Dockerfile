# Use the existing QIIME 2 image
FROM sebimer/samba-v4-qiime2:2024.2

# Set writable cache directory for Matplotlib
ENV MPLCONFIGDIR=/tmp/matplotlib

# Set working directory
WORKDIR /qiime2

# Ensure Micromamba is used correctly (fix /bin/sh issue)
SHELL ["/bin/bash", "-c"]

# Fix QIIME 2 cache issue
RUN rm -rf ~/.cache/qiime2 ~/.config/qiime2 && \
    micromamba run -n qiime2-2024.2 qiime dev refresh-cache

# Fix UMAP and Numba issues
RUN micromamba run -n qiime2-2024.2 micromamba install -c conda-forge umap-learn numba -y

# Ensure QIIME 2 loads all plugins correctly
RUN micromamba run -n qiime2-2024.2 qiime dev refresh-cache

# Set entrypoint to a known working shell
ENTRYPOINT ["/bin/bash"]

