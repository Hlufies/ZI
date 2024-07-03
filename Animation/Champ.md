# Install
1. conda create -n champ python=3.10
2. conda activate champ
3. pip install -r requirements.txt

# 2024/7/3
## 测试Champ，一些问题
1. 将视频和参考图像拟合以获取SMPL信息的原因或意义是什么？  
SMPL远不止是一个网格模型。它在工业界和学术界都有广泛应用。因此，SMPL的应用范围扩展了Champ的下游应用。例如，有许多从文本（或音频）到SMPL、文本到纹理贴图的工作，这些都可以轻松集成到Champ的推理过程中。如果你熟悉Blender，你可以使用Champ做很多有创意的事情。你可以尝试这个CEB Blender插件。  
2. 使用获取的视频SMPL通过Blender渲染的动作序列与实际视频的动作不同，原因是什么？此外，我们如何才能使它与实际视频的动作尽可能相似？  
是的，它们并不是完全对齐的。你可以参考人类网格恢复（Human Mesh Recovery）的相关工作，以跟进最新的技术状态（SOTA）。不过，实际上我们在Champ中使用的4D-Humans已经具有足够的准确性和鲁棒性，除了手部和面部表情。如果你想要更逼真的动作，可以尝试直接预测深度、法线，并使用来自SMPL的语义图。

## 待解决的问题
1. 复杂的background（缺失一致性）  
Disentangling Foreground and Background Motion for Enhanced Realism in Human Video Generation
Disentangled Control for Realistic Human Dance Generation
2. 人脸  
IP-Adapter, Photomaker, InstantID  
ID-Animator: Zero-Shot Identity-Preserving Human Video Generation  
3. 手指  
感觉虽然用SMPL可以提高动作对其，但是手指细节还是没办法解决  
4. 衣服细节和皮肤质感  
Champ里面细节不够，有点过度拟合Conditions  
有些论文里面用到canny，提取图像的edge：CTRL-Adapter: An Efficient and Versatile Framework for Adapting Diverse Controls to Any Diffusion Model
## 方案
SMPL-X
https://smpl.is.tue.mpg.de/index.html   
https://github.com/vchoutas/smplx/tree/main  
![img_v3_02ce_2368f827-c326-4910-84b4-042e8f14e96g](https://github.com/Hlufies/ZI/assets/130231524/86408347-3a25-4f06-86ab-d4aeed78e70f)



