# -CalculateFactorial
# -计算不超过20的整数的阶乘
![我的截图](image/屏幕截图%202025-06-08%20201323.png)

![我的截图的绝对路径版本](https://raw.githubusercontent.com/C-Anderson-C/-CalculateFactorial/main/image/屏幕截图%202025-06-08%20201323.png)
```cpp

#include<iostream>
#include<cmath>
#include<string>
#include<stdexcept>
using namespace std;


unsigned long long  CalculateFactorial(int n) { //因为计算结果数值过大，普通int无法容纳；unsigned无符号，负数没有阶乘

	unsigned long long foral = 1;
		for (int i = 1;i <= n;i++) {  //n由main中获取，从1乘到n来计算该数阶乘
			foral=foral* i;
	}
		return foral; //返回计算结果
}


int main() {
	while (true) {
		string input;  //将输入转换为字符串
		cout << "请输入一个小于20的整数数以计算阶乘（按q结束程序）：" << endl;
		getline(cin, input);  //获取一整行的输入

		if (input == "q") {  //完成结束程序条件
			cout << "程序结束" << endl;
			break;
		}
		try {
			size_t pos;  //负数无阶乘，size_t是无符号整数，与int是相同功能但int有符号
			int number = stoi(input,&pos);  //利用stoi函数将字符串转换为整数，pos指针将指向第一个非整数字符前一位

			if (number < 0) {
				throw invalid_argument("负数没有阶乘!");
			}
			if (number > 20) {
				throw invalid_argument("输入的数不能大于20");
			}
			if (pos != input.length()) {
				throw invalid_argument("你的输入并不是整数!");
			}
			unsigned long long result = CalculateFactorial(number);
			if (CalculateFactorial(number)) {
				cout << number << "的阶乘是：" << result << endl;
			}

		}
		catch (const invalid_argument&e) {
		    cout <<"错误!"<<" "<< e.what() <<" "<< "请输入非负整数！" << endl;
	}
		catch (const out_of_range& e) {
			cout << "错误!"<< " " << e.what() <<" "<< "输入的数超出int范围！" << endl;
		}

	}
	

}
