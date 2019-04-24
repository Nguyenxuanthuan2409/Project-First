# Project-First
Đây là dự án nghiên cứu đầu tiên của tôi.
// Nguyen Xuan Thuan
// 24/09/1999
// Chuong trinh dat ve may bay gom 13 hang va 6 ghe	A B C D E F
// Ky hieu: *: cho con trong	X: cho da dat

#include <iostream>
#include <ctime>
const int MAX = 100;
using namespace std;

void NhapMang(char NhapMang[][MAX], int hang, int cot) ;
void XuatMang(char NhapMang[][MAX], int hang, int cot);
void BangDatVe(char NhapMang[][MAX],int hang, int cot, int hangchon, int cotchon);
void menu(char NhapMang[][MAX], int hang, int cot);

int main() 
{
	char a[MAX][MAX];
	int hang = 13, cot = 6;
	char Tiep;		
	NhapMang(a, hang, cot);		// khong goi ham xuat mang vi trong menu da xuat 1 lan r
	do {
		menu(a, hang, cot);		// chua ham xuat mang
		cout << "\nBan co muon tiep tuc dat ve hay khong (y : yes, n : no): ";
		cin >> Tiep;
	} while (Tiep == 'y' || Tiep == 'Y');
	if ( Tiep == 'N' || Tiep == 'n' )
		cout <<"Chao tam biet quy khach. Hen gap lai quy khach vao mot ngay khong xa.\n ";
	system("pause");
	return 0;
}

void NhapMang(char NhapMang[][MAX], int hang, int cot) 
{
	srand(time(NULL));
	int ranDom = 0;
	for (int i = 0; i < hang; i++)
	{
		for (int j = 0; j < cot; j++)
		{
			if ((ranDom = rand() % 100) <= 50)		// Khoi tao so ngau nhien: neu ra so <= 50 thi in dau *, ngc lai in X
			{
				NhapMang[i][j] = '*';//MA ASKII dau * la 42
			}
			else
			{
				NhapMang[i][j] = 'X';// Tuong tu X : 88
			}

		}
	}
}
void XuatMang(char NhapMang[][MAX], int hang, int cot)
{
	cout << "\t";			// Khoang trang phia tren hang 1 va ben trai ki tu A
	for (char i = 'A'; i <= 'F'; i++)
	{
		cout << i << "\t";			// chay ky tu chu cai tu A ===> F
	}
	cout << endl;
	for (int i = 0; i < hang; i++)		// chay dong 
	{
		cout << "Hang " << i + 1 << "\t";
		for (int j = 0; j < cot; j++)
		{
			cout << NhapMang[i][j] << "\t";
		}
		cout << endl;
	}
}
void BangDatVe(char NhapMang[][MAX],int hang, int cot, int hangchon, int cotchon)
{
	if (NhapMang[hangchon - 1][cotchon - 1] == '*')		// neu mang a[i][j] = * thi gan lai = X
	{
		NhapMang[hangchon - 1][cotchon - 1] = 'X';		// -1 de xu ly giao dien nguoi dung
		cout << "\nBan da dat ve thanh cong. Xin kiem tra lai vi tri ban dat!\n";
		cout << "Neu khong chinh xac vui long lien he bo phan cham soc khach hang cua chung toi theo so: 0962741977\n";
		cout << "Xin chan thanh cam on quy khach.\n";
		XuatMang(NhapMang, hang, cot);		// xuat lai mang cho nguoi dung kiem tra vi tri minh dat
	}
	else 
	{
		cout << "\nHien tai vi tri ban chon da co nguoi dat, xin chon ghe khac";
	}
}
void menu(char NhapMang[][MAX], int hang, int cot)
{
	int chon = 0;
	int chonhang = 0, choncot = 0;
	do {
		cout << "\n---------Ban hay nhap vao loai ve-----------";
		cout << "\n----------1.Thuong gia----------------------";
		cout << "\n----------2.Pho thong-----------------------";
		cout << "\n----------3.Tiet kiem-----------------------";
		cout << "\nLua chon cua ban: ";
		cin >> chon;
		if (chon <= 0 || chon > 3) 
		{
			cout << "\nBan chon sai hay kiem tra lai!";
		}
		else 
		{
			cout << "\nThong tin ghe tren may bay nhu sau: ";
			cout << "\nMay bay co 13 hang va moi hang co 6 ghe";
			cout << "\nBang dat ve hien tai nhu sau ( *: cho con trong- X: cho da dat):\n";
			XuatMang(NhapMang, hang, cot);

			switch (chon) 
			{
			case 1:
				{
				do {
					cout << "\nBan chon loai ve la thuong gia va ban hay chon vi tri ghe nam trong hang 1 va hang 2: ";
					cout << "\nHang: ";
					cin >> chonhang;
					cout << "\nGhe: ";
					cin >> choncot;
					if ((chonhang <= 0 || chonhang > 2) || (choncot <= 0 || choncot > 6)) 
					{
						cout << "\nBan nhap sai ghe xin xem lai thong tin!";
					}
					else 
					{
						BangDatVe(NhapMang, hang, cot, chonhang, choncot);
					}
				} while ((chonhang <= 0 || chonhang > 2) || (choncot <= 0 || choncot > 6));
				break;
			}
			case 2: {
				do {
					cout << "\nBan chon loai ve la pho thong va ban hay chon vi tri ghe nam trong hang 3 den hang 7: ";
					cout << "\nHang: ";
					cin >> chonhang;
					cout << "\nGhe: ";
					cin >> choncot;
					if ((chonhang < 3 || chonhang > 7) || (choncot <= 0 || choncot > 6)) 
					{
						cout << "\nBan nhap sai ghe xin xem lai thong tin!";
					}
					else 
					{
						BangDatVe(NhapMang, hang, cot, chonhang, choncot);
					}
				} while ((chonhang < 3 || chonhang > 7) || (choncot <= 0 || choncot > 6));
				break;
			}
			case 3: {
				do {
					cout << "\nBan chon loai ve la tiet kiem va ban hay chon vi tri ghe nam trong hang 8 den hang 13: ";
					cout << "\nHang: ";
					cin >> chonhang;
					cout << "\nGhe: ";
					cin >> choncot;
					if ((chonhang < 8 || chonhang > 13) || (choncot <= 0 || choncot > 6)) 
					{
						cout << "\nBan nhap sai ghe xin xem lai thong tin!";
					}
					else
					{
						BangDatVe(NhapMang, hang, cot, chonhang, choncot);
					}
				} while (chonhang < 8 || chonhang > 13 || choncot <= 0 || choncot > 6);
				break;
			}
			}
		}
	} while (chon <= 0 || chon > 3);
}
