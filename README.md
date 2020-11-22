# DroneMSDK
# 背景
1.随着无人机成本的降低和技术与管理法规的成熟，无人机的应用范围越来越广，比如农药喷洒、电线维修与监测、地理探测等。然而，随着无人机行业的应用越来越广，合格的无人机飞手已经供不应求。

# 目的
1.为了提升无人机飞行员的技术水平，培养合格的行业飞手，提出开发无人机模拟教学系统。教学系统通过设置不同的科目如起飞、降落、悬停和航线飞行等，帮助飞行员积累飞行经验，评测飞行水平。

1. 本项目测试机型为大疆的mavic air2，遥控器为不带屏遥控器。（带屏遥控器是无法使用大疆SDK的）
2. 集成使用要点：
	1. 需先测试手机下载大疆专用APP DJI GO 4进行无人机的对频操作，此时应该注意，每次将手机和无人机进行USB连接时，会弹出默认启动应用弹框，应选择仅次一次；不然后续装上自己的应用后，连上无人机是无法拉起我们自己的应用的。
	2. 当连接成功，可以正常起飞后，此时装入自己的应用，启动并执行 DJIModel中的 startRegisterSDK 方法，执行注册大疆SDK。
	3. 注册成功后，会弹出登录弹框，提示登录大疆账号，此时应填入自己的大疆账号（国内每三个月登录一次，国外不受此限制）
	4. `setDjiProductStateCallBack`是回调产品数据，当存在产品时，会执行`onAirPlaneStateChange（bool）`方法，传入参数为true
	5. 此时可以调用videoPreview方法，传入surfaceView，来执行无人机摄像头数据预览
	6. 也可以通过设置`setDjiVideoDataCallBack`回调，来获取无人机回传的H264数据，获取H264数据时，视频预览会静帧
	7. 通过`setAirPlaneCameraParam`方法，来设置无人机摄像头参数，具体参数请查看`DJICameraParams`类，其中有详细的说明

# 如何启动
1.ide选择android studio(https://developer.android.com/studio)。安装完之后会自动下载sdk，如果提示找不到包的仓库地址，把vpn设置为全局模式。

# 踩坑
1.提示*No variants found for 'app'. Check build files to ensure at least one variant exists.*。解决方法：选择settings，搜索android sdk，在sdk中下载android 8.0

