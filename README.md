# -CalculateFactorial
# -计算不超过20的整数的阶乘
```cpp

#include<iostream>
#include<cmath>
#include<string>
#include<stdexcept>
using namespace std;


unsigned long long  CalculateFactorial(int n) {

	unsigned long long foral = 1;
		for (int i = 1;i <= n;i++) {
			foral=foral* i;
	}
		return foral;
}


int main() {
	while (true) {
		string input;
		cout << "请输入一个小于20的整数数以计算阶乘（按q结束程序）：" << endl;
		getline(cin, input);

		if (input == "q") {
			cout << "程序结束" << endl;
			break;
		}
		try {
			size_t pos;
			int number = stoi(input,&pos);

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