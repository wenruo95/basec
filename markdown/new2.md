
http://wiki.ubuntu.org.cn/UbuntuManual:%E7%BD%91%E7%BB%9C%E8%AE%BE%E7%BD%AE#.E7.AC.AC_10_.E7.AB.A0_-_.E7.BD.91.E7.BB.9C.E8.AE.BE.E7.BD.AE




	public static double getRandomMoney(RedPackage _redPackage) {
	    // remainSize 剩余的红包数量
	    // remainMoney 剩余的钱
	    if (_redPackage.remainSize == 1) {
	        _redPackage.remainSize--;
	        return (double) Math.round(_redPackage.remainMoney * 100) / 100;
	    }
	    Random r     = new Random();
	    double min   = 0.01; //
	    double max   = _redPackage.remainMoney / _redPackage.remainSize * 2;
	    double money = r.nextDouble() * max;
	    money = money <= min ? 0.01: money;
	    money = Math.floor(money * 100) / 100;
	    _redPackage.remainSize--;
	    _redPackage.remainMoney -= money;
	    return money;
	}

LeftMoneyPackage数据结构如下：

	class RedPackage {
	    int    remainSize;
	    double remainMoney;
	}

测试时初始化相关数据是：

	static void init() {
	    redPackage.remainSize  = 30;
	    redPackage.remainMoney = 500;
	}
