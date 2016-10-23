开放接口API
===============
开发对外接口，供客户端APP使用，或者提供给第三方站点
discuz自带的mobile插件主要提供给掌上论坛使用，不大适合对外API

注册
----------------
discuz为了防止恶意注册，注册form表单的name为随机生成的字符串，后台防灌水--基本设置--注册表单名称设置, 结果无效
，代码里写死了逻辑

::

    $reginputbwords = array('username', 'password', 'password2', 'email');
	
    if(in_array($data['reginput']['username'], $reginputbwords) || !preg_match('/^[A-z]\w+?$/', $data['reginput']['username'])) {
		$data['reginput']['username'] = random(6);
	}

如果开发注册接口给客户端，这里就不能有这样的逻辑，建议将$reginputbwords改为空数组