+++
title = "资源分享"
date = 2024-05-01T10:00:00+08:00
draft = false
ShowToc = false  # <--- 加上这一行，强制关闭这篇文章的目录
+++

<!-- 整个卡片背景，加上 class 用来控制样式 -->
<div class="resource-card" style="background: rgba(255, 255, 255, 0.85); padding: 30px; border-radius: 16px; backdrop-filter: blur(10px); margin-top: 20px; box-shadow: 0 8px 20px rgba(0,0,0,0.2);">

<!-- 强制将内部所有文字、标题、段落和链接变为深灰色 -->
<div style="color: #333 !important;">
    <p style="color: #333 !important;">这里是我分享的一些照片和文档，点击即可查看或下载。</p>

    <h2 style="color: #333 !important;">📄 文档下载</h2>
    <ul>
        <li><a href="/docs/Anthropic-Detecting-and-countering-091026.pdf" style="color: #0066cc !important; text-decoration: underline; font-weight: bold;">📥 点击下载：Anthropic 汇报</a></li>
    </ul>

    <h2 style="color: #333 !important;">📸 照片分享</h2>
    <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 15px; margin-top: 20px;">
        <img src="/photos/pixel-art.png" alt="像素操操操" onclick="window.open(this.src)" style="width: 100%; height: 200px; object-fit: cover; border-radius: 12px; cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.1);">
        <img src="/photos/roseshun.png" alt="玫瑰顺飞" onclick="window.open(this.src)" style="width: 100%; height: 200px; object-fit: cover; border-radius: 12px; cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.1);">
    </div>
</div>

</div>