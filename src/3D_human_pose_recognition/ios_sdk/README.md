# 项目 README

## 1. 模型加载

要使用此项目，请联系我们获取 SDK 和接口文档，以便加载模型和进行初始化配置。

## 2. 模型 3D 点位结果优化

### 滤波器

为了优化模型的 3D 点位结果，本项目集成了多种滤波器：

#### 1. 卡尔曼滤波器：

- **类名**：`KalmanFilter`
- **使用方式**：`DiscreteKalmanFilter`
- **继承**：`BaseKalmanFilter`

#### 2. 低通滤波器：

- **类名**：`LowPassFilter`

#### 3. 一欧滤波器：

- **类名**：`OneEuroFilter`

### 人体骨骼结构定义：

- **类名**：`HumanBodyBone`  
  定义了人体骨骼的 3D 结构和骨骼点位。

### 滤波器的使用（主函数）：

- **类名**：`MoveNetSample`
  - 函数：`predictPose3D`
  - 功能：接收 3D 点位数据流，初始化所需的滤波器，对模型结果进行实时滤波处理。

## 3. IK 系统（逆向运动学）

在 IK 系统中，滤波后的 3D 点位数据将转换为关节的旋转数据和坐标数据，用于驱动模型。

### 文件结构：

- **`HumanBodyBones.json`**：
  - 内置的骨骼 T-pose 模型，用于表示模型的初始骨骼姿态。
- **`AvatarManager`**：

  - 功能：管理骨骼点位映射，调用 `ModelData` 加载内置骨骼结构。

- **`AvatarBonePoint`**：
  - 定义骨骼的相关信息，如父子关节关系、关节旋转等。

---

通过集成的卡尔曼滤波器、低通滤波器、一欧滤波器，以及 IK 系统的逆向运动学实现，可以有效地优化人体骨骼点位和关节旋转数据的精度。
