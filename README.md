Outlook 全自动注册工具（云码API版）🤖
 
Python开发的Outlook无人值守注册工具，集成云码验证码API，多环境适配，全程自动化运行✨
 
核心能力⚡
 
- 云码API深度集成（余额检测/识别重试/结果校验）
- 无头模式默认运行，适配「云服务器/安卓CJ_IDE/Windows/Linux」
- 进程守护/故障自愈/防风控/代理自动轮换/资源自动清理
- 账号去重保存📝，运行/错误日志分离🔍，问题排查超方便
 
前置准备📦
 
1. 云码官网注册账号并充值，获取用户名/密码
2. 环境：Python 3.8+ + Chrome/Chromium浏览器（安卓仅需Chrome内核）
 
快速使用🚀
 
1. 安装依赖
 
bash
  
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple selenium requests schedule python-dotenv webdriver-manager loguru psutil
 
 
2. 配置.env（同目录创建，仅填3项必填）
 
env
  
VERIFY_API_TYPE=jfbym
JFBYM_USERNAME=你的云码账号
JFBYM_PASSWORD=你的云码密码
 
 
3. 启动运行
 
bash
  
# 测试运行（验证配置/环境）
python outlook_register.py --once
# 后台常驻（Linux/安卓/云服务器）
nohup python outlook_register.py > run.log 2>&1 &
# Windows后台运行
start pythonw outlook_register.py
 
 
核心文件📂
 
plaintext
  
├── outlook_register.py  # 主程序文件
├── .env                 # 配置文件（自建）
├── pass.txt             # 注册成功账号（自动生成，邮箱 密码 格式）
├── outlook_register.log # 运行日志
└── error.log            # 错误日志
 
 
多环境适配📱💻☁️
 
- 安卓CJ_IDE：ChromeDriver放 /sdcard 目录，直接运行程序即可
- 本地测试： .env 加一行 HEADLESS=False ，可视化查看运行流程
- 云服务器：后台运行，配合宝塔/面板进程守护更稳定
 
日志排查🔧
 
bash
  
tail -f outlook_register.log  # 实时看运行日志
tail -f error.log            # 实时看错误日志
 
 
注意事项⚠️
 
1. 云码余额不足会自动暂停运行，需及时充值💸
2. 连续失败15次触发风控，程序自动暂停10分钟后恢复
3. 免费代理稳定性差❌，建议用付费代理池提升成功率✅
4.  pass.txt 为明文保存，服务器端执行 chmod 600 pass.txt 限制文件权限
 
