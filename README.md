# intelligent-closestool
一款实用stm32f0芯片,采用st公司的HAL库及freeRTos为基础来开发的智能马桶主板软件,(包含软件硬件).采用市场较为流行的即热式模块.

# pcb
pcb部分使用easyeda https://lceda.cn/editor#id=0ef7880f5eed44a698f3014726256795
这是此次的电路板,部分电阻值可能没用修改,发现时修改.各位也可以给我留言
pcb部分推荐可以做部分优化,在12v控制q1,q2,q3,q4,q5的开关管都加一个下拉电阻,还有蓝牙模块可以更换为2.4g模块,类似nref24l01,就可以正常通用数据库.


#app flutter
手机app进去后修改conBan.dart页面的


var _BTid = /*"98:5D:AD:1D:57:5A"*/ "00:15:83:00:AB:00" ;

如果你不知道的模块的id,可以联机运行一下,软件会print扫描到的蓝牙的id,然后改进去就可以运行了.
然后健康数据传输过去的时间暂时会不准,暂时不知道是不是手机设置问题.也没打算很详细去改正,准备后面以正常的遥控+wifi联网,然后控制和健康数据分开走,并加入个人习惯的温度,风温等更加详细的记录.

#其他内容见wiki

#已知未修改bug
按键里面次序有严重错误,建议要运行删除里面事件,等手头项目做完,再次修改.(已经修复)

按键事件会跟用于hold电池开关的动作冲突,准备一起大改.按原电路设计,暂时取折中方法,冲水除了停电冲水,其他时候不hold着dcs_pin.这样如果冲水过程中断电会造成冲水不停,得重新按一下冲水按键.

目前打算把这一块独立出来,脉冲阀工作电压6v就可以很稳定了.并且停电时也保持有大冲和小冲.

风温档位会导致计时器停止(因为设置了计时器为0时计时器停止,项目结束后一起更新)
