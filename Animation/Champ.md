# Install
1. conda create -n champ python=3.10
2. conda activate champ
3. pip install -r requirements.txt
# Inference  
## Isuse
1. 将视频和参考图像拟合以获取SMPL信息的原因或意义是什么？  
SMPL远不止是一个网格模型。它在工业界和学术界都有广泛应用。因此，SMPL的应用范围扩展了Champ的下游应用。例如，有许多从文本（或音频）到SMPL、文本到纹理贴图的工作，这些都可以轻松集成到Champ的推理过程中。如果你熟悉Blender，你可以使用Champ做很多有创意的事情。你可以尝试这个CEB Blender插件。  
2. 使用获取的视频SMPL通过Blender渲染的动作序列与实际视频的动作不同，原因是什么？此外，我们如何才能使它与实际视频的动作尽可能相似？  
是的，它们并不是完全对齐的。你可以参考人类网格恢复（Human Mesh Recovery）的相关工作，以跟进最新的技术状态（SOTA）。不过，实际上我们在Champ中使用的4D-Humans已经具有足够的准确性和鲁棒性，除了手部和面部表情。如果你想要更逼真的动作，可以尝试直接预测深度、法线，并使用来自SMPL的语义图。
