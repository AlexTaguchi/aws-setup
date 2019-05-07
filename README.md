# aws-setup
Setup for a deep learning environment on AWS

### Running the AWS Instance
- Select the Deep Learning AMI launch instance (Ubuntu Version 22.0)
- The g-series GPUs are a bit old, and the p-series ones are nicer (p3.2xlarge is a single Volta GPU)
- Add the .pem file to keychain on Mac:
```bash
ssh-add -K ~/path_to_pem/my_pem_file.pem
```
(make sure permissions are set right with chmod 700 my_pem_file.pem)
- Login to AWS instance with ssh ubuntu@##.###.##.###
- Mount the AWS instance for easy local access:
  - Install FUSE and SSHFS on Mac (https://osxfuse.github.io/)
  - Mount AWS instance: sudo sshfs ubuntu@##.###.##.###:~ ~/path_to_mnt -o allow_other,defer_permissions

### Installing a deep learning environment
- Activate a PyTorch deep learning environment:
```bash
source activate pytorch_p36
```
- Upgrade to the most recent verison of PyTorch:
```bash
conda install pytorch torchvision cudatoolkit=10.0 -c pytorch
```
- Install PyTorch Geometric if desired:
```bash
pip install --verbose --no-cache-dir torch-scatter
pip install --verbose --no-cache-dir torch-sparse
pip install --verbose --no-cache-dir torch-cluster
pip install --verbose --no-cache-dir torch-spline-conv (optional)
pip install torch-geometric
```
