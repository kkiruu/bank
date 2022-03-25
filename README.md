/*This is Bank ATM machine Program that handles ATM operations like:
1. 1. Check Account Balance
2. 2. Deposit Money in an Account.
3. 3. WithDraw Money from Account.
4.  
5. A customer will need to Enter his Account number and ATM Pin to access the Account Operations.
6. This Program is using a dummy account number 12345 and dummy Pin number 54321
7. */
8. #include <iostream>
9. using namespace std;
10.  
11. int CustomerAccountNumber = 12345;
12. int pinNumber = 54321;
13. int AccountBalance = 0;
14.  
15. bool ValidateCustomerDetails() {
16.  
17.     int InputAccountNumber = -1;
18.     int InputPinNumber = -1;
19.     bool isAccountInvalid = true;
20.     bool isPinInvalid = true;
21.  
22.     cout << "Welcome!" << endl;
23.  
24.     while (isAccountInvalid) {
25.  
26.         cout << "Please enter your Bank account number: ";
27.         cin >> InputAccountNumber;
28.  
29.         if (InputAccountNumber == CustomerAccountNumber) {
30.             isAccountInvalid = false;
31.         }
32.         else {
33.             cout << "Invalid Account Number! Try again." << endl;
34.         }
35.     }
36.     int RetryCount = 3;
37.     while (isPinInvalid && RetryCount) {
38.  
39.         cout << "Enter your Customer PIN: ";
40.         cin >> InputPinNumber;
41.  
42.         if (InputPinNumber == pinNumber) {
43.             isPinInvalid = false;
44.         }
45.         else {
46.             RetryCount--;
47.             if(RetryCount)
48.                 cout << "Invalid Customer PIN number! Try again." << endl;
49.             else
50.             {
51.                 cout << "Your Account is Locked! 3 retry Reached! Try After some time." << endl;
52.                 return false;
53.             }
54.  
55.         }
56.  
57.     }
58.  
59.     return true;
60.  
61. }
62. int DisplayMenu() {
63.  
64.     int UserInputOption = -1;
65.  
66.     cout << "Welcome to Your Account!! Please choose Option to Proceed" << endl;
67.     cout << "    1 - View Your Account balance" << endl;
68.     cout << "    2 - Withdraw Cash" << endl;
69.     cout << "    3 - Deposit Cash" << endl;
70.     cout << "    4 - Exit" << endl;
71.     cout << "Enter an Option to Proceed: " << endl;
72.     cin >> UserInputOption;
73.  
74.     return UserInputOption;
75.  
76. }
77. void DisplayAccountBalance() {
78.  
79.     cout << "You Account Balance is:" << endl;
80.     cout << "$" << AccountBalance << endl;
81.  
82. }
83.  
84. void WithDrawMoneyFromAccount() {
85.  
86.     int UserInputOption = -1;
87.     int valueToWithdraw = 0;
88.     long CustomerRequest = 0;
89.     bool isNotFinished = true;
90.  
91.     do {
92.  
93.         cout << "Withdrawal options:" << endl;
94.         cout << "1 - $20" << endl;
95.         cout << "2 - $40" << endl;
96.         cout << "3 - $60" << endl;
97.         cout << "4 - $100" << endl;
98.         cout << "5 - $200" << endl;
99.         cout << "6 - cancel transaction" << endl;
100.         cout << "7 - Custom Amount" << endl;
101.         cout << "choose a withdrawal option (1-7)" << endl;
102.  
103.         cin >> UserInputOption;
104.         switch (UserInputOption) {
105.         case 1:
106.             valueToWithdraw = 20;
107.             break;
108.         case 2:
109.             valueToWithdraw = 40;
110.             break;
111.         case 3:
112.             valueToWithdraw = 60;
113.             break;
114.         case 4:
115.             valueToWithdraw = 100;
116.             break;
117.         case 5:
118.             valueToWithdraw = 200;
119.             break;
120.         case 6:
121.             isNotFinished = false;
122.             break;
123.         case 7:
124.             cout << "Enter Amount to WithDraw:" << endl;
125.             cin >> CustomerRequest;
126.             valueToWithdraw = CustomerRequest;
127.             isNotFinished = false;
128.             break;
129.         default:
130.             cout << "Invalid option! Try again." << endl;
131.             break;
132.         }
133.  
134.         if (valueToWithdraw != 0) {
135.             if (valueToWithdraw > AccountBalance) {
136.                 cout << "Sorry!! Your Account Balance is Only $" << AccountBalance << ". You can't withdraw $" << valueToWithdraw << endl;
137.             }
138.             else {
139.                 AccountBalance = AccountBalance - valueToWithdraw;
140.                 isNotFinished = false;
141.             }
142.             valueToWithdraw = 0;
143.         }
144.  
145.     } while (isNotFinished);
146.  
147. }
148. void DepositMoneyInAccount() {
149.  
150.     int UserInputOption = -1;
151.     bool isNotFinished = true;
152.     long depositAmount = 0;
153.  
154.     do {
155.  
156.         cout << "Cash Deposit Options. Please Enter Your Selection" << endl;
157.         cout << "1 - $20" << endl;
158.         cout << "2 - $40" << endl;
159.         cout << "3 - $60" << endl;
160.         cout << "4 - $100" << endl;
161.         cout << "5 - $200" << endl;
162.         cout << "6 - cancel transaction" << endl;
163.         cout << "7 - Custom Amount" << endl;
164.         cout << "Choose a deposit option (1-7)" << endl;
165.  
166.         cin >> UserInputOption;
167.         switch (UserInputOption) {
168.         case 1:
169.             AccountBalance = AccountBalance + 20;
170.             isNotFinished = false;
171.             break;
172.         case 2:
173.             AccountBalance = AccountBalance + 40;
174.             isNotFinished = false;
175.             break;
176.         case 3:
177.             AccountBalance = AccountBalance + 60;
178.             isNotFinished = false;
179.             break;
180.         case 4:
181.             AccountBalance = AccountBalance + 100;
182.             isNotFinished = false;
183.             break;
184.         case 5:
185.             AccountBalance = AccountBalance + 200;
186.             isNotFinished = false;
187.             break;
188.         case 6:
189.             isNotFinished = false;
190.             break;
191.         case 7:
192.             cout << "Please Enter Amount to Deposit:" << endl;
193.             cin >> depositAmount;
194.             AccountBalance = AccountBalance + depositAmount;
195.             isNotFinished = false;
196.             break;
197.         default:
198.             cout << "Invalid option! Try again." << endl;
199.             break;
200.         }
201.  
202.     } while (isNotFinished);
203.  
204. }
205.  
206. int main() {
207.  
208.     if (ValidateCustomerDetails()) {
209.  
210.         int isNotFinished = true;
211.  
212.         do {
213.  
214.             switch (DisplayMenu()) {
215.             case 1:
216.                 DisplayAccountBalance();
217.                 break;
218.             case 2:
219.                 WithDrawMoneyFromAccount();
220.                 break;
221.             case 3:
222.                 DepositMoneyInAccount();
223.                 break;
224.             case 4:
225.                 isNotFinished = false;
226.                 break;
227.             default:
228.                 cout << "Invalid option! Try again." << endl;
229.                 break;
230.             }
231.  
232.         } while (isNotFinished);
233.  
234.     }
235.  
236.     return 0;
237.  
238. }
239. Conclusion :
240. This is the full source code for the Bank ATM machine Project in C++, We can use it in the assignment projec
