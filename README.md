# Cadastro_de_Devedores
 
unit Unit1;

interface

uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Variants, System.Classes, Vcl.Graphics,
  Vcl.Controls, Vcl.Forms, Vcl.Dialogs, Vcl.StdCtrls, Vcl.ExtCtrls;

type
  TCadastro = class(TForm)
    Panel1: TPanel;
    Panel2: TPanel;
    Panel3: TPanel;
    Panel4: TPanel;
    Edit1: TEdit;
    Edit2: TEdit;
    Panel5: TPanel;
    Button1: TButton;
    Label1: TLabel;
    Label2: TLabel;
    Panel6: TPanel;
    Panel7: TPanel;
    Panel8: TPanel;
    Shape2: TShape;
    Shape3: TShape;
    Shape4: TShape;
    Button3: TButton;
    Button4: TButton;
    Button2: TButton;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Panel9: TPanel;
    Panel10: TPanel;
    ListBox1: TListBox;
    Panel11: TPanel;
    ListBox2: TListBox;
    ListBox3: TListBox;
    Shape1: TShape;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button4Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
    procedure pAdicionar;
  end;

var
  Cadastro: TCadastro;

implementation

{$R *.dfm}

{ TForm1 }

procedure TCadastro.Button1Click(Sender: TObject);
  var
  x: string;
  y: string;
  msg: string;
begin
  {se nao tiver nada escrto nos edits, ele vai nos mostrar uma imagem
  no momeno em que aprtamos o botao ADD}
    x:=Edit1.Text;
    y:=Edit2.Text;
  if (x='') or (y='')then
  begin
    msg := 'Você precisa informar o nome e o valor!';
    ShowMessage(msg)
  end
  else
    pAdicionar;

end;

procedure TCadastro.Button2Click(Sender: TObject);
var
  index : integer;
begin
  index:=Listbox1.itemIndex;
  Listbox1.Items.Delete(index);
  Listbox2.Items.Delete(index);
  Listbox3.Items.Delete(index);
end;

procedure TCadastro.Button3Click(Sender: TObject);
var
  index:integer;
  msg:string;
begin
  index:= Listbox1.ItemIndex;
  if (Listbox3.Items[index] = 'DEVENDO') then //Valida se a pessoa está nos devendo
    msg:=Listbox1.Items[index] + ' me deve ' + Listbox2.Items[index] + '.'
  else
    msg:= 'A conta selecionada já foi paga!';
    showmessage(msg);
end;

procedure TCadastro.Button4Click(Sender: TObject);
var
  index: integer;
begin
  //Captura o item da lista selecionado
  index := Listbox1.ItemIndex;
  Listbox3.Items[index]:= 'PAGO';
end;

procedure TCadastro.pAdicionar;
begin
  Listbox1.Items.Add(Edit1.Text);
  Listbox2.Items.Add('R$' + Edit2.Text);
  ListBox3.Items.Add('DEVENDO');
  Edit1.Text:= '';
  Edit2.Text:= '';
end;

end.
