# delphi_projem
# ilk-projem

Bu proje, Delphi kullanılarak oluşturulmuş bir personel kargo giriş ekranıdır.  
Kargoların desi hesabı yapılmakta, personel ve kargo bilgileri ile ilgili gönderen ve alıcı bilgileri tutulmaktadır.  
Kayıtlar arasında listeleme yapılabilmekte ve tüm veriler Access veri tabanında saklanmaktadır.

## Özellikler
 -Giriş ekranı
- Kargo giriş ekranı
- Desi hesabı
- Personel, kargo, gönderen ve alıcı bilgileri kaydı
- Kayıtları listeleme
- Access veri tabanında veri saklama

## Kullanım

Projeyi Delphi'de açarak gerekli ayarları yapabilirsiniz. Access veri tabanının yolunu belirtmeyi unutmayın.

## Örnek Kodlar
var
  Form3: TForm3;

implementation

{$R *.dfm}
uses unit2,unit1;
procedure TForm3.SpeedButton1Click(Sender: TObject);
 var

   en,boy,yuk,ag, cap:Integer;
    des:Real;
   ücret:Currency;
begin
   Adotable3.First;
    repeat
     Adotable3.Edit;
     ag:=Adotable3.FieldByName('Ürün Ağırlığı').AsInteger;
     yuk:=Adotable3.FieldByName('Ürünün Yüksekliği').AsInteger;
     en:=Adotable3.FieldByName('Ürünün Eni').AsInteger;
     boy:=Adotable3.FieldByName('Ürünün Boyu').AsInteger;
     Adotable3.FieldByName('des').AsFloat:=(ag*yuk*en*boy)/3000;

     if(Adotable3.FieldByName('des').AsFloat<=1 ) and (Adotable3.FieldByName('des').AsFloat>0 )then
      begin
     Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*30;
     end
     else if (Adotable3.FieldByName('des').AsFloat<=2) and (Adotable3.FieldByName('des').AsFloat<1)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*35;
       end
        else if (Adotable3.FieldByName('des').AsFloat<=3) and (Adotable3.FieldByName('des').AsFloat<2)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*40;
       end
        else if (Adotable3.FieldByName('des').AsFloat<=4) and (Adotable3.FieldByName('des').AsFloat<3)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*45;
       end
        else if (Adotable3.FieldByName('des').AsFloat<=5) and (Adotable3.FieldByName('des').AsFloat<4)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*50;
       end
        else if (Adotable3.FieldByName('des').AsFloat<=6) and (Adotable3.FieldByName('des').AsFloat<5)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*55;
         end
         else if (Adotable3.FieldByName('des').AsFloat<=7) and (Adotable3.FieldByName('des').AsFloat<6)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*60;
       end
       else if (Adotable3.FieldByName('des').AsFloat<=8) and (Adotable3.FieldByName('des').AsFloat<7)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*65;
       end
       else if (Adotable3.FieldByName('des').AsFloat<9) and (Adotable3.FieldByName('des').AsFloat<8)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*70;
       end
   else if (Adotable3.FieldByName('des').AsFloat<10) and (Adotable3.FieldByName('des').AsFloat<9)then
      begin
       Adotable3.FieldByName('Ücret').AsCurrency:=adotable3.FieldByName('des').AsFloat*75;


      end ;
       adotable3.Post;
       adotable3.next;
       until (adotable3.eof);



end;

procedure TForm3.SpeedButton2Click(Sender: TObject);
begin
 Adotable1.Insert;
 Adotable2.Insert;
 Adotable3.Insert;
end;

procedure TForm3.SpeedButton3Click(Sender: TObject);
begin
Adotable1.delete;
Adotable2.delete;
Adotable3.delete;
end;

procedure TForm3.SpeedButton4Click(Sender: TObject);
begin
   Adotable1.Post;
   Adotable2.Post;
   Adotable3.Post;
end;




procedure TForm3.SpeedButton5Click(Sender: TObject);
begin
   form1.show;
   form3.Close;
end;

procedure TForm3.SpeedButton6Click(Sender: TObject);
begin
adotable1.Refresh;
adotable2.Refresh;
adotable3.Refresh;
end;

end.

