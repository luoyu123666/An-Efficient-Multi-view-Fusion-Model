# An-Efficient-Multi-view-Fusion-Model
# Requirements
Python 3, pytorch > 1.2+ and pytorch < 1.4
pip install -r requirements.txt
conda install pytorch cudatoolkit=10.0 -c pytorch
# Pretrained weights download
mkdir outs
cd datasets/
bash get_pretrained_models.sh
Please follow the instructions in datasets/README.md for preparing the dataset
# Training
python main.py --cfg path/to/config
tensorboard --logdir outs/

# Testing
python main.py --cfg configs/xxx.yaml DOTRAIN False
# Visualization
Human 3.6M input visualization
python main.py --cfg configs/epipolar/keypoint_h36m.yaml DOTRAIN False DOTEST False EPIPOLAR.VIS True  VIS.H36M True SOLVER.IMS_PER_BATCH 1
python main.py --cfg configs/epipolar/keypoint_h36m.yaml DOTRAIN False DOTEST False VIS.MULTIVIEWH36M True EPIPOLAR.VIS True SOLVER.IMS_PER_BATCH 1
# Human 3.6M prediction visualization
# generate images
python main.py --cfg configs/epipolar/keypoint_h36m_zresidual_fixed.yaml DOTRAIN False DOTEST True VIS.VIDEO True DATASETS.H36M.TEST_SAMPLE 2
# generate images
python main.py --cfg configs/benchmark/keypoint_h36m.yaml DOTRAIN False DOTEST True VIS.VIDEO True DATASETS.H36M
