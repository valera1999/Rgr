# Rgr
unit Unit2;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Grids, StdCtrls;

type
  TForm1 = class(TForm)
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Label6: TLabel;
    Label7: TLabel;
    Label8: TLabel;
    Edit1: TEdit;
    Edit2: TEdit;
    Edit3: TEdit;
    Edit4: TEdit;
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    StringGrid1: TStringGrid;
    Label9: TLabel;
    Edit5: TEdit;
    Label10: TLabel;
    Edit6: TEdit;
    Edit7: TEdit;
    Label11: TLabel;
    Edit8: TEdit;
    Label12: TLabel;
    Label13: TLabel;
    Label14: TLabel;
    Label15: TLabel;
    Label16: TLabel;
    Label17: TLabel;
    Label18: TLabel;
    Label19: TLabel;
    Label20: TLabel;
    Edit9: TEdit;
    Edit10: TEdit;
    Edit11: TEdit;
    Edit12: TEdit;
    Edit13: TEdit;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

procedure TForm1.Button1Click(Sender: TObject);
Type
  Tm=Array[1..10]of real;
  Tk=Array[1..10,1..10]of real;
Var
  Mx,Ma:Tm;
  My:Tk;
  A,Xn,Xk,Dx,An,Ak,Da,c,d,e,res:real;
  k,N,Km,i:integer;
function g(x:real):real;
  begin
  g:=exp(x)-2*(x-1)*(x-1);
  end;
procedure Uravn(c,d,e:real;Km:integer;var res:real;i:integer);//Описание ПП URAVN
var
k,n:integer;
dx,x:real;
begin
k:=0;
n:=1;
while k<Km do
begin
x:=c;
n:=n*2;
dx:=(d-c)/n;
while x<=d do
if (abs(0-g(x))<e) and (x>0) then
begin
i:=k;
k:=Km;
res:=x;
x:=d+dx;
end
else
x:=x+Dx;
k:=k+1;
end;
end ;
procedure Tab(An,Ak,Xn,Dx,Da:real;Var Mx,Ma:Tm;My:Tk);//Описание ПП TAB
var
  i,j,N:integer;
   y,X:real;
  begin
  A:=An;
  i:=1;
  while A<=Ak do
  begin
  Ma[i]:=A;
  X:=Xn;
  for j := 1 to N  do
  begin
  if x>4 then
  Y:=(sin(a*x)/cos(a*x))*cos(res)
  else
  Y:=sqrt(x)*sqrt(a*x*a*x+(ln(1)*ln(1)));  //Здесь должно быть Y:=exp(x*ln(b/res))*sqrt(a*x*a*x+(ln(res)*ln(res)))
  Mx[i]:=X;
  My[i,j]:=Y;
  X:=X+Dx;
  end;
  i:=i+1;
  A:=A+Da;
  end;
  end;
  procedure RezOut(k,N:integer;Var Mx,Ma:Tm;My:Tk);//Описание ПП RezOut
  Var
  i,j:integer;
  A:real;
  begin 
for i:=1 to N do
begin 
with Form1.StringGrid1 do 
begin 
Cells[i,0]:= FloatToStrF(Ma[i],ffFixed,5,3);
end; 
end;

for j:=1 to K do
begin 
with Form1.StringGrid1 do 
begin
Cells[0,j]:= FloatToStrF(Mx[j],ffFixed,5,3); 
end; 
end;

for i:=1 to N do
for j:=1 to K do 
begin
with Form1.StringGrid1 do 
begin 

Cells[i,j]:= FloatToStrF(My[i,j],ffGeneral,7,5);
end;

  {for i := 1 to k  do
  begin
    StringGrid1.Cells[i,0]:=('A['+IntToStr(i)+']='+FloatToStr(Ma[i]));
        for j := 1 to N  do
    begin
      if(StringGrid1.ColCount<j+1)then
        StringGrid1.ColCount:=StringGrid1.ColCount+1;
        StringGrid1.Cells[0,j]:=('x['+IntToStr(j)+']='+FloatToStr(Mx[j]));
        StringGrid1.Cells[i,j]:=FloatToStrF(My[i,j],ffGeneral,6,5);
    end;
    If(StringGrid1.RowCount<i)then
      StringGrid1.RowCount:=StringGrid1.RowCount+1;   }
      end;
      end;

  begin
  An:=StrToInt(Edit1.Text);
  Ak:=StrToInt(Edit2.Text);
  Da:=StrToInt(Edit3.Text);
  Xn:=StrToInt(Edit4.Text);
  Xk:=StrToInt(Edit5.Text);
  Dx:=StrToInt(Edit6.Text);
  N:=StrToInt(Edit7.Text);
  c:=StrToInt(Edit8.Text);
  d:=StrToInt(Edit9.Text);
  e:=StrToFloat(Edit10.Text);
  Km:=StrToInt(Edit11.Text);
  {A:=StrToFloat(Edit1.Text);}
  K:=trunc((Ak-An)/Dx+1);
  StringGrid1.ColCount:=1+N;
  StringGrid1.RowCount:=k+1;
  with Form1.StringGrid1 do
  begin
  Cells[0,0]:='X\A';
  end;
N:=trunc((Xk-Xn)/Dx);
Uravn(c,d,e,Km,res,i);//Вызов ПП Uravn
Tab(An,Ak,Xn,Dx,Da,Mx,Ma,My);//Вызов ПП Tab
RezOut(k,N,Mx,Ma,My);//Вызов ПП RezOut
end;
procedure TForm1.Button3Click(Sender: TObject);
begin
Close;
end;


procedure TForm1.Button2Click(Sender: TObject);
var
i:integer;
begin
Edit1.Text:=''; Edit2.Text:='';
Edit3.Text:=''; Edit4.Text:='';
Edit5.Text:=''; Edit6.Text:='';
Edit7.Text:=''; Edit8.Text:='';
Edit9.Text:=''; Edit10.Text:='';
Edit11.Text:=''; Edit12.Text:='';
Edit13.Text:='';
with Form1.StringGrid1 do
begin
  for i := FixedCols to ColCount - 2 do
  Cols[i].Clear;
end;
end;
end.
