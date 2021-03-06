# Liscript

**�� - �������� ��������� :)**

��������� ����� ����� ��� ���������� ������� ���� ���������������� Clojure � ������ ������������� � ������������� ����� �������. �� ������ �������� �� Clojure � ����� ������ SICP � ������� ����������� ���� ������������� �������� �����, ��� ������� ��������� ���������� � ��� ���������. � ���������� ��������� ����, ������� � � ����� ��������� ��������� ������ � ������ Liscript :)
  
� �������� ����� ���������� � ������ Haskell, ������ ��� ����� ����������� ���������������� � ��� ��� ������� ���� ������. ����������, �������� ����� ���� ����������� ���������� ��� ����������������, �� ������ �������� ����������� �������� ����������, ����������� ������, ������������� ��������������� ������ � ������ �������������� � ������ �������� ������ �����. �������, ��������, � ���������� Liscript ��� ��������� ```let``` - �� �������� ��������� ```def```, ��� ```if ... then ... else``` - �� �������� ```cond```  � �.�. ������, ������ ��� ������������� ����� ������ ����� (���������� ������� �����), � ��� ����� ������� � ������������ ������� �� ����� ������������ ����������� ������, � ���� ��������� ���������� �������� ��������� ������ ��� ��������� �������.
  
��� ���������� ������� �� ��������� - ��� ���������� ����������� ���������-���������, ������ ���� 20 ������ ��������� ���������� �� ���������, ��� ����������� ��������� ��������, �������� ������ � �.�. �� ���� ������ �����, ����� ��� ���� ����� ��������, ������ � ����� �� ����������� �� ��� ���� ���������������� ��� ���������, � ���� ��� ��������� ��������� �� ��� "��" - �������� (�����) ��������� :)
� ����� ��������������, ������ ����������� ����������" � ���������� ���������� ��������� ��������� ����� ������������ �� ���� ������ https://github.com/Ivana-/Liscript
� ����� � ���������� �� ������ ���������� � ������������ � ��������� ������������ ���������� ��������������.
 
**������� ��������������**

- ������� ���� � ������� �� ��������, ���������������� ����������� ����������
-  ����������� ���������� ���������� � ������� ������-������ (����� �������)
-  ������������� �������, ��������� �������, ����������� ���������
-  ������������� ����������� ������� (������� ������� ����������)
-  ������ ������ - ����������� ������������� ����������� ���������
-  ����������� ���������� �������� � �������������� ������� (��� ���������� ����������� ��� ������)
-  �������� ���������� � ��������������� (�� ����� ������� � ��������)

 
**�������������� - �����, �������**
 
� ���� �������������� ����������� ����� ������, ������� �� ��������������� ��������� � ��������������. �� ������ ����� ������, ��������� ������� ������ ����� ������, � ������ ������ ������ ���� ���� "����������", � ������� ���������� ��������� ����� � ��������� ������� � ���� ����, ������� ����� ��������. ����� ����� ���������� txt � ������ ������ ����� � ������ ���� (��� ������� � �������������� GHCi) ��� ����� �� ���������������� exe ������ - ��� ������� ����������������� ��������������. � ��������� ������ ����� ��������������� ������ ������� ����� �������� �� ������������ � ����� ������, ����� ���� ��������� ����� ���������.
 
��� ������. ����� � ����� ������ ����������� ����������, � ��������� �� ��� ������ https://en.wikibooks.org/wiki/Write_Yourself_a_Scheme_in_48_Hours
������ ������, �������� ���� ���������� � �� �����, � ������ �������� ��� �� �����������. � ����� � ������ ���������� ������ ��� ```LispVal``` � ��� ��������, �� � �� ��������. ������ �� ��� ���������� �� ���������� ```Parsec```. � ���������� ������������ ��� ��� ����� ����, �� �� ����� � ��� �����������, � � ���������� ��� ���� ������� ����� �������� ���� ������ - �� ������ � ����� ������� AST, ���� ������ �������������� �������������� �� ����� �������������. ��� ����� ������� �������� 20 (!) ����� (������ ���������� � ��������).

**���� - ��������� � ����������**

����� ���� �� ��������, ��� � ����� ������ ������������ Liscript �������� ����������� ����� �������������� ������, � � �����-�� ������� ��� ����� ������� ������ - ��� �������� ���������� ��������� �� ������������ �����, ��� ���� ������ �� ��������� � ������ ���������. �� � ������ ������� �� ����� ��������� �������, ��� ��� ���������� �������������� ���� � ������������ ����������� ����� - ������� :) ���������, ������ ��� ���. ���, ������� ����� ��������� ��������� �����, ����������� ���:
 ```haskell
 data LispVal = Atom String
              | List [LispVal]
              | Func { params :: [String], body :: [LispVal], closure :: Env }
              | Macr { params :: [String], body :: [LispVal] }
 ```
������, ���������, ������ �������. ���� �������� 2 ��������� �����, ������� �� ���������� �����, �� ������ ���� - ��� ���������� ���-�������� �����, � ������ - ������, ���������� �������� ������ (�� ����������� ������������) ����. �� ����, ���������� ��������� ������������ - ������, � ���������� ��� ���� - ������. ��� �������������� ������� ������ ��������� ������ ��������� ���������� ```Atom String``` ����� ������, ������� �� ���������� ��� ������, ������� ��� ������� - � ```"abc"```, � ```2```, � ```3.5```. �� ����� ��� ���������� ���������� ����������� �������� ���� �������� ���������� ��� ���� ���������� �� ��������� - ```++``` ������� ��������� ��������, ```+``` ������ �������, � ```+'``` ������� � ��������� ������, �������������� ����� ���������� �������� � ���� ����� ����� ����������� �������� � ����������� ��������� � ������ ����������. � ���� ������ ��� ���������� �������� �������� ���������� ��� ��������, �� ��� ������������ ��������� �����������, ��� �� �������� � �������.
 
����� �� ������� �����? ���������� - �������� ����� ��� ```Atom Int``` � ```Atom Double```, ��� ������� ������ ��������� ����� ���������� � ����� ��� ������ ����� ��������, � �.�. � ���������� ��� ����� �������� ������� ��� ��������� �������� - ��� �� ���� ��������� ���������� �� ����� � � ������. � ����� ��� ����� ����� ������� ����������� �������� ����� - �� ������������ ���������, �� ��� ����� ����������� ������ ������� ��������������, � ����� ���� - ������ �� ����������� �����, ������ ������������. �� � ������������ � �� ��� ������ ����� ������� ������� ����������, ������� ������ ��������������.
     
**���� - ������� � �������**

������� �������� ������������ ��������� ������� ������ ����� - �� ���� �� ����� ���������� � �������� ���������� � ���������� � �������� �������� �� �������, �������������� ��������������������, �� ������ ��� ����� ���������, ����� ��������� ��������� �������. ��� ���������� ������� ������������ ����� �� �������� - ������� ��������������� (������ �� �������, � ������� �� Scheme, ��������) ����������� �������� ����������, ��� �������� ����������� � ������� ���������� ���������� � ����� �������� �����-��������� (��. ������ ��� ������ ������), � ����� � ���� ��������� ����������� ���� ������� - ��� ������� SICP. ����������� ��������� ������� � ����� ������ � ������ ����������� ���������� � ����� ��������� �� �������������� (��������� ����������� ������ �������� ����������), �������� ���������� �� ��������� - ����. ����������� ��������� �������� ��� � ������������ � ��.

������� - �����������, �� ���� � ������������ � ����������� �� ����� ������������� ���������. ��� � ������� - ��� ������ ���������� ��� �� �������, �� ������� �� ������� ������������ �� ���������� ���� - ����� ���� ������������� � ����������. ��������� �������� ���� ����, � ��� ������� ��� ����� ��� �� �������, � �������� F-���������. �� ��� ������ �������, ����� ���������, � �� ��������� ����� �� ������������ �� ������� - ����������� � 2 �����, � ��������� ������, �� ���� ������ ��������� (� ������� �� �������, ��� ���������). �� � ������� �� ������ ������ ������, � Liscript ������� ����� ��� � ������� �������� ��������� ������� ������. ��� ������������ � ���� ����� ������� ����� ��������
http://matt.might.net/articles/metacircular-evaluation-and-first-class-run-time-macros/
(��������� ��� ������ ����� ����� ����������).   

**������ ������ - ����� ���� �� ����������**

��� ���������� ����� ����������, ��� ����������� �������, ��������� ���������� �������� � ������������� �������, � ���������� ���-�� ������� ��� �����. � �������� ������ ��������� ������� �������� ��������� Map ���� - ��������, ��� � �������� ������ ��������� �����:
```haskell
type Frame = Map.Map String LispVal -- ���� ���������� ���� ����-��������
```
������ ����� ��������� �������� ������� ������ � ����������� �������. �� ��� ���������� ��������� �������� ��������� ���� (��������, ���������� ����������� �������) ��������� ������������ ������� ��������� ��������, ��������� � ����� � ��� �� ���������� ������, ������� ��������� ���������, �������� ��������� ����� ��������-������.

� �������������� �������� ���������-����������� ���� ������ ��������, �������� �� ���� �������� ��� ���������� � �������� ������ ������ ���������� ����, �������� ����� ���� �� ������� ������ ��� ����� � ������� � ������ ��� ��� ������ �� ������� - ������ ����� ����������, � ���������� ���� - ����������� �������� � ����� ��������� ������ ������. ������� ������ �������� �� ����� ������������� ���� ������ �� ������� ���������� ����� � ���������� ��������, ���� �� �������� - ���������� ��� ��������� � �������� ������ (��� ���������� �������� ���������������, ��� � ������� �����), ������� ��������� �������� �������� �� ������ �� �������� (������ ������ �� ������ ���� �� �������� ������ ����� �� � ����� �����), ������� ����������� ������ ���������� ��������� ����� ������ (��� �������� ������������) � ������ ������ � ����� ������� ����� �����. � ����� ������� ������ ��������, ��������� ����������� ��������� � �������, � �.�. � �����������, ����� ������ ������� - ����������� ������������ ���������, �� ���� ����� � ���������� ���������� ������� ������������ ������ �������, ������� ������� ���� �������� ���������� ����-�������� �� ������ ������ ��������. �� ����, ��������� ������ ������� - ���������, �������, � �.�. �����������, ����� ������� ����������� �� �����������, ���� �������� ������� ��� ���������� � ������ �������.

�� ��� �������� ����������� ����������� ���������, � � ������ ������ ������ � ���� �� ���������� �� ������� ���������, ������� � � ������ ������������ � SICP ������ ����������� ��������� ������, � ������� ������ ���� ���� ������������� �������� � ��� ����� ������� ������ ����������� ������, ������ ��� ��������� ������ ������������ ����� ���������, ������� ������ ���� ���������� ����� �� ����� ������ ���������� - � ���������� �� ����� ����������� ��������� ������
  ```haskell
   data Env = NullEnv | Voc (IORef Frame, Env) -- ������ ������ �������-��������
   ```
�������������� ������ ������� ��� ������ � ������� (������, ������ � ��������) �������� ����������, �.�. �� ������� ������ � ��� ������ ���� ���� � ����� ����� ��������� (������������ �����), � ��������� ������ �������� ����� ��� ���� �������. ��� ����� ������ ������ ��� ����� �������� ����� � �������, ������� ��������� ������ ������ �����������, �������-�� ������� ����� ������������ ��������� ������� ������ �����, ������ ������� ```eval``` �������� ������� � ������ ```IO``` � ���������� �� ��� ������ ������ ������ �� ������ ���� � ������. ������� ������ �� ���������� � ������������ � �� :)
 
**���������� �����**
 
� ���������� ������ ���� ������� :) ���, � ������� �� ��������, ��� �����-������ �������� ������������� ������ � ������������ ���� ��� ��� ����� ���������� ����. �� ���� �������������� ������ � ��������, ���������� �������� ����� ������������, � ���� ����� ���� �� Liscript ��������� ��������� � ������� (��������, �������� ������, ���������� �����������������, �������� ������-������ � �.�.) - � ��� ��� ����� ��� �� Haskell, ������ ��� ���� ����������� ���������, �������� ������� � �.�. :) � ���� � ���� ����� �������� ������� ��� �����������/����������� �� ����� ��������, ����� �������� �� Liscript, ����� ���� �� Haskell ��� ��� ����, � ��������� �������/���������� ��������.

�� � ��, Clojure ���-���� �� �������� ������ ������� :)
