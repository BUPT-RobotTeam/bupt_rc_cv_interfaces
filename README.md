# 2023届与图像处理相关的所有自定消息类型
> 你可以随意更改代码然后push到仓库中
>
> 文章写于2024年4月5日

## 环境要求
> 1. ROS2 (作者使用的平台是humble)

## msg关系图
```bash
┌───────────────────────┐       ┌───────────────────────┐
│                       │       │                       │
│     CVInferenceArray  │       │       CVCameras       │
│                       │       │                       │
│  - inference_result   │       │  - cam_type (uint8)   │
│    (CVInference[])    │       │  - cam_fps (float64)  │
│                       │       │                       │
│  - img (CVFrame)      │       └───────────────┬───────┘
│                       │                       │
└───────────────┬───────┘                       │
                |───────────────────────────────│
        ┌───────┴───────────────┐               │
        │                       │               │
        │       CVInference     │               │
        │                       │               │
        │  - track_id (int32)   │               │
        │  - tlwh (float32[])   │               │
        │  - score (float32)    │               │
        │                       │               │
        └───────────────────────┘               │
                                                │
                                  ┌─────────────┴─────────────┐
                                  │                           │
                                  │          CVFrame          │
                                  │                           │
                                  │  - frame_width (uint16)   │
                                  │  - frame_height (uint16)  │
                                  │  - frame_data (uint8[])   │
                                  │                           │
                                  └───────────────────────────┘
```