

[�հ�](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)  

__�հ�__  
�հ����ɺ����Լ������ú����Ĵʷ�������϶��ɡ������������������հ�����ʱ���ܷ��ʵ����оֲ�������  

	function makeAdder(x){
		return function(y){
			return x+y;
		};
	}

	var add5 = makeAdder(5);
	var add10 = makeAdder(10);

	console.log(add5(2));
	console.log(add10(2));


�ӱ����Ͻ���makeAdder ��һ���������� �� �������˽�ָ����ֵ�����Ĳ��������͵ĺ������������ʾ���У�����ʹ�ú������������������º��� �� һ����������� 5 ��ͣ���һ���� 10 ��͡�


ʹ�ã�  
*ʹ�ñհ�����������  
*�ñհ�ģ��˽�з���--ʵ���������غͷ�װ  

