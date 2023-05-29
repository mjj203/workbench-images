FROM quay.io/opendatahub-contrib/workbench-images:cuda-jupyter-datascience-c9s-py39_2023b_latest

USER 0

RUN yum -y install cuda-toolkit-11-8 && \
    yum -y clean all  --enablerepo='*'
ENV XLA_FLAGS=--xla_gpu_cuda_data_dir=/usr/local/cuda


USER 1001

RUN echo "Installing softwares and packages" && \
    pip install torch==2.0.1 --index-url https://download.pytorch.org/whl/cu118 && \
    pip install transformers==4.29.2 einops==0.6.1

# Fix permissions to support pip in Openshift environments
RUN chmod -R g+w /opt/app-root/lib/python3.9/site-packages && \
    fix-permissions /opt/app-root -P
