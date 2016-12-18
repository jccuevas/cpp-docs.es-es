---
title: "Error del compilador C2664 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2664"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2664"
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2664
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': no se puede convertir el argumento n de 'type1' a 'type2'  
  
 Este problema de conversión de parámetros puede suceder si se crea una instancia de una clase y se trata de realizar una conversión implícita en un constructor marcado con la palabra clave `explicit`.  Para obtener más información sobre las conversiones explícitas, consulte [Conversiones](../../cpp/user-defined-type-conversions-cpp.md).  
  
 Si se pasa un objeto temporal a una función que toma una referencia a un objeto como parámetro, dicha referencia debe ser una referencia `const`.  
  
 Si se pasa a la función un parámetro cuyo tipo no es el que espera la función, se crea un objeto temporal mediante el constructor correspondiente.  A continuación se pasa ese objeto temporal a la función.  En ese caso, el objeto temporal se utiliza para inicializar la referencia.  En versiones anteriores del lenguaje, todas las referencias se podían inicializar mediante objetos temporales.  
  
 Para corregir el error C2664:  
  
-   Vuelva a comprobar el prototipo de la función dada y corrija el argumento citado en el mensaje de error.  
  
-   Proporcione una conversión explícita si es necesario.  
  
 El error C2664 también se puede generar si una clase oculta un miembro en una de sus clases base.  
  
 Para obtener más información, consulte [Cómo: Convertir System::String en wchar\_t\* o char\*](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C2664 y se muestra cómo corregirlo.  
  
```  
// C2664.cpp  
// C2664   
struct A {  
   void f(int i) {};  
};  
  
struct B : public A {  
   // To fix, uncomment the following line.  
   // using A::f;  
   void f(A a) {};  
};  
  
int main() {  
   B b;  
   int i = 1;  
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.  
}  
```  
  
## Ejemplo  
 En este ejemplo también se genera el error C2664 y se muestra cómo corregirlo.  
  
```  
// C2664b.cpp  
// C2664 expected  
struct A {  
   // To fix, uncomment the following line.  
   // A(int i){}  
};  
  
void func( int, A ) {}  
  
int main() {  
   func( 1, 1 );   // No conversion from int to A.  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el error C2664 que se genera al usar un literal de cadena para llamar a `Test` y se muestra cómo corregirlo.  Dado que el parámetro es una referencia `szString`, el constructor correspondiente debe crear un objeto.  El resultado es un objeto temporal que no se puede usar para inicializar la referencia.  
  
```  
// C2664c.cpp  
// compile with: /EHsc  
// C2664 expected  
#include <iostream>  
#include <string.h>  
using namespace std;  
  
class szString {  
   int slen;  
   char *str;  
  
public:  
   szString(const char *);  
   int len() const {   
      return slen;   
   }  
};  
  
// Simple reference cannot bind to temp var.  
void Test(szString &a) {}  
  
// To fix, uncomment the following line.  
// void Test(const szString &a) {}  
  
szString::szString(const char * newstr) : slen(0), str(NULL) {  
   slen=strlen(newstr);  
   str = new char[slen + 1];  
   if (str)  
      strcpy_s(str, (slen + 1), newstr);  
}  
  
int main() {  
   Test("hello");  
}  
```  
  
## Ejemplo  
 El compilador impone los requisitos estándar de C\+\+ para que se aplique `const`.  Este ejemplo genera el error C2664:  
  
```  
// C2664d.cpp  
// C2664 expected  
#include <windows.h>  
  
void func1(LPCSTR &s)  
{  
  
}  
  
void func2(LPSTR &s)  
{  
   func1(s);  
}  
  
int main()  
{  
   return 0;  
}  
```  
  
## Ejemplo  
 A continuación se muestra una situación más compleja en la que se genera el error C2664, con instrucciones sobre cómo solucionarlo:  
  
```  
// C2664e.cpp  
// compile with: /EHsc  
// C2664 expected  
#define _INTL  
#include <locale>  
#include <iostream>  
  
using namespace std;  
#define LEN 90  
  
int main( ) {  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
  
   // To fix, delete the following line.  
   char* pszNext;  
  
   // To fix, uncomment the following line.  
   // const char* pszNext;  
  
   wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");    
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).in( state,  
      pszExt, &pszExt[strlen(pszExt)], pszNext,  
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   // See earlier comment.  
      pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error) ?   
                       L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
  
   exit(-1);  
}  
```  
  
## Ejemplo  
 Una variable de enumeración no se convierte en un tipo subyacente capaz de satisfacer la llamada a la función.  Para obtener más información, vea la [enum class](../../windows/enum-class-cpp-component-extensions.md).  En el ejemplo siguiente se genera el error C2664 y se muestra cómo corregirlo.  
  
```  
// C2664f.cpp  
// compile with: /clr  
using namespace System;  
public enum class A : Char {  
   None = 0,  
   NonSilent = 1,  
};  
  
void Test(Char c) {}  
  
int main() {  
   A aa = A::None;  
   Test(aa);   // C2664  
   Test(Char(aa));   // OK - fix by using a conversion cast  
}  
```  
  
## Ejemplo  
 Un error en el compilador MIDL provoca la emisión de un tipo wchar\_t como unsigned short en la biblioteca de tipos.  Para resolver este error, convierta el tipo en su código fuente de C\+\+ o defina el tipo como una cadena en el archivo idl.  
  
```  
// C2664g.idl  
import "prsht.idl";  
  
[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]  
  
interface IMyObj1 : IUnknown {  
   HRESULT  teststr([in, string] wchar_t *wstr);  
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);  
   HRESULT  testbstr([in] BSTR bstr);  
};  
  
[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]  
library myproj1 {  
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]  
   coclass CMyObj1 { interface IMyObj1; };  
}  
```  
  
 El error C2664 también se genera si se utiliza `wchar_t` al trasladar código de Visual C\+\+ 6.0 a versiones posteriores.  En Visual C\+\+ 6.0 y versiones anteriores, `wchar_t` era `typedef` para `unsigned short` y, por consiguiente, podía convertirse implícitamente en ese tipo.  En versiones posteriores a Visual C\+\+ 6.0, `wchar_t` es su propio tipo integrado, tal y como se especifica en el estándar de C\+\+, y ya se puede convertir implícitamente en `unsigned short`.  Consulte [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C2664 y se muestra cómo corregirlo.  
  
```  
// C2664h.cpp  
#import "C2664g.tlb"  
using namespace myproj1;  
  
int main() {  
   IMyObj1Ptr ptr;  
  
   wchar_t * mybuff = 0;  
   BSTR bstr = 0;  
   int len;  
   ptr->teststr(mybuff);  
   ptr->testbstr(bstr);  
   ptr->testarr(mybuff, len);   // C2664  
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast  
}  
```  
  
## Ejemplo  
 El error C2664 también se produce si el compilador no puede deducir los argumentos de plantilla.  
  
```  
// C2664i.cpp  
#include <stdio.h>  
template <class T, int iType=0>  
class CTypedImg {  
public:  
   CTypedImg() {}  
   void run() {}  
  
   operator CTypedImg<T>& () {  
      return *((CTypedImg<T>*)this);  
    }  
};  
  
template <class t1>  
void test(CTypedImg<t1>& myarg) {  
   myarg.run();  
}  
  
int main() {  
   CTypedImg<float,2> img;  
  
   test((CTypedImg<float>&)img);   // OK  
   test<float>(img);   // OK  
   test(img);   // C2664 - qualify as above to fix  
}  
```