# 手机端银离子荧光定量分析与使用说明

这是一个独立的 Streamlit 网页项目，包含“开始检测”和“使用说明”两个标签，不依赖原网站地址。

## 功能

- 上传两张 DNG 原始图像，或通过浏览器直接拍照。
- 在第一张图上框选空白与样品分析区域，将相同坐标用于第二张图。
- 通过左右互换校正预测银离子浓度，查看计算详情并下载中文 CSV。
- 五步真实手机操作截图教程、输入方式说明和常见问题。

固定模型定量范围为 2–12 μM。网页拍照模式与 DNG 模型的一致性尚未完成验证。教程截图中的 5.62 μM 是该次操作结果，不是所有样品的预期结果。每张 DNG 上传上限为 1024 MB，实际可处理大小受服务器资源限制。

## 独立部署到 Streamlit Community Cloud

### 第一步：创建新的 GitHub 仓库

1. 登录 GitHub，点击右上角加号，选择 New repository。
2. 仓库名称建议填写 `Ag_mobile_camera_guide`，不要覆盖或删除原来的 `Ag_mobile_camera_test` 仓库。
3. 按需要选择仓库可见性，点击 Create repository。仓库与应用的可见性分别按实际需要配置。
4. 进入新仓库，通过上传现有文件入口，上传本项目文件。
5. 上传 `streamlit_app.py`、`requirements.txt`、`README.md` 和整个 `guide_images` 文件夹，保持文件夹层级。
6. 点击 Commit changes。不要直接上传 ZIP，不要把项目外层文件夹也套入仓库。

新仓库根目录应为：

    streamlit_app.py
    requirements.txt
    README.md
    guide_images/
        01_upload.jpg
        02_blank.jpg
        03_sample.jpg
        04_result.jpg
        05_details.jpg

### 第二步：创建新的 Streamlit 应用

1. 打开 https://share.streamlit.io/ ，使用与新仓库关联的 GitHub 账号登录。
2. 创建新应用，选择刚才的新仓库和实际使用的分支。
3. 主程序路径填写 `streamlit_app.py`。
4. 在高级设置中选择 Python 3.11（若平台提供此选项）。
5. 新网址可以尝试 `ag-mobile-camera-guide`，以平台提示的可用性为准；不要选择覆盖原应用。
6. 点击 Deploy，等待依赖安装和启动。完成后以平台实际返回的网址为准。

### 第三步：核对

- 顶部出现“开始检测”和“使用说明”两个标签。
- 使用说明中的五张图像正常显示。
- 使用一组真实 DNG 文件完成上传、框选和预测，下载 CSV。
- 原网站仍可通过原网址访问。

原网站：https://ag-mobile-camera-test.streamlit.app/

## 本地预览

在本项目目录运行：

    py -m pip install -r requirements.txt
    py -m streamlit run streamlit_app.py

## 项目文件

`streamlit_app.py` 是独立网页入口，计算常数已包含在程序中。本项目无需上传建模脚本、实验工作簿或测试 DNG 文件。`guide_images` 仅包含图文教程所需的原始截图。
