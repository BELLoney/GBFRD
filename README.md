# GBFRD
Xinyu Su, **Zhong Yuan***, Baiyang Chen, Dezhong Peng, Hongmei Chen, and Yingke Chen,[Detecting anomalies with granular-ball fuzzy rough sets](Paper/2024-GBFRD.pdf), Information Sciences, June 2024, DOI: [10.1016/j.ins.2024.121016](https://doi.org/10.1016/j.ins.2024.121016). (Code)

## Abstract
Most of the existing anomaly detection methods are based on a single and fine granularity input pattern, which is susceptible to noisy data and inefficient for detecting anomalies. Granular-ball computing, as a novel multi-granularity representation and computation method, can effectively compensate for these shortcomings. We utilize the fuzzy rough sets to mine the potential uncertainty information in the data efficiently. The combination of granular-ball computing and fuzzy rough sets takes into account the benefits of both methods, providing great application and research value. However, this novel combination still needs to be explored, especially for unsupervised anomaly detection. In this study, we first propose the granular-ball fuzzy rough set model, and the relevant definitions in the model are given. Subsequently, we pioneeringly present an unsupervised anomaly detection method based on granular-ball fuzzy rough sets called granular-ball fuzzy rough sets-based anomaly detection (GBFRD). Our method introduces the granular-ball fuzzy rough granules-based outlier factor to characterize the outlier degree of an object effectively. The experimental results demonstrate that GBFRD exhibits superior performance compared to the state-of-the-art methods. The code is publicly available at https://github.com/Mxeron/GBFRD.

## Framework
![image](Paper/GBFRD_Framework.png)

## Usage
You can run GBFRD.py:
```
if __name__ == '__main__':
    load_data = loadmat('./Example.mat')
    trandata = load_data['trandata']
    ID = (trandata >= 1).all(axis=0) & (trandata.max(axis=0) != trandata.min(axis=0))
    scaler = MinMaxScaler()
    if any(ID):
        trandata[:, ID] = scaler.fit_transform(trandata[:, ID])
    data = trandata[:,:-1]
    label = trandata[:,-1]
    sigma = 0.6
    out_factors = GBFRD(data, sigma)
    print(out_factors)
```
You can get outputs as follows:
```
out_factors = [0.20595384 0.30457415 0.1775164  0.37436982 0.22177716 0.22989089
 0.30296993 0.26581625 0.27651796 0.2649136  0.31455997 0.26370036
 0.27206448 0.25388759 0.26026712 0.2736494  0.27872721 0.25322572
 0.31623681 0.24653541]
```
## Citation
If you find GBFRD useful in your research, please consider citing:
```
@article{SU2024121016,
title = {Detecting anomalies with granular-ball fuzzy rough sets},
author = {Xinyu Su and Zhong Yuan and Baiyang Chen and Dezhong Peng and Hongmei Chen and Yingke Chen},
journal = {Information Sciences},
volume={646},
pages = {121016},
year = {2024},
doi = {https://doi.org/10.1016/j.ins.2024.121016},
publisher={Elsevier}
}
```
## Contact
If you have any questions, please contact suxinyu@stu.scu.edu.cn or yuanzhong@scu.edu.cn.
