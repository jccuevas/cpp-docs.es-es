---
title: Funciones de &lt;ios&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 91e10200576389edcaff55860da3a8a701e75bab
ms.lasthandoff: 02/24/2017

---
# <a name="ltiosgt-functions"></a>Funciones de &lt;ios&gt;
||||  
|-|-|-|  
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[dec](#dec)|  
|[fixed](#fixed)|[hex](#hex)|[internal](#internal)|  
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|  
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|  
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|  
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|  
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|  
|[unitbuf](#unitbuf)|[uppercase](#uppercase)|  
  
##  <a name="a-nameboolalphaa--boolalpha"></a><a name="boolalpha"></a>  boolalpha  
 Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como **True** o **False** en el flujo.  
  
```  
ios_base& boolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las variables de tipo `bool` se muestran como 1 o 0.  
  
 `boolalpha` llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::boolalpha`) y, después, devuelve ` str.`  
  
 [noboolalpha](../standard-library/ios-functions.md#noboolalpha) invierte el efecto de `boolalpha`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_boolalpha.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   bool b = true;  
   cout << b << endl;  
   boolalpha( cout );  
   cout << b << endl;  
   noboolalpha( cout );  
   cout << b << endl;  
   cout << boolalpha << b << endl;  
}  
```  
  
```Output  
1  
true  
1  
true  
```  
  
##  <a name="a-namedeca--dec"></a><a name="dec"></a>  dec  
 Especifica que las variables de entero aparezcan en notación de base 10.  
  
```  
ios_base& dec(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las variables de entero se muestran en base 10.  
  
 **dec** llama eficazmente a ` str``.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::dec`**, ios_base::basefield**) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_dec.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 100;  
  
   cout << i << endl;   // Default is base 10  
   cout << hex << i << endl;     
   dec( cout );  
   cout << i << endl;  
   oct( cout );  
   cout << i << endl;  
   cout << dec << i << endl;  
}  
```  
  
```Output  
100  
64  
100  
144  
100  
```  
  
##  <a name="a-nameiosdefaultfloata--ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a>  &lt;ios&gt; defaultfloat  
 Configura los indicadores de un objeto `ios_base` para que utilicen un formato de presentación predeterminado para valores float.  
  
```  
ios_base& defaultfloat(ios_base& _Iosbase);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Iosbase`  
 Un objeto `ios_base`.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama eficazmente a _I `osbase.`[ios_base::unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)`(ios_base::floatfield)` y, después, devuelve _I `osbase`.  
  
##  <a name="a-namefixeda--fixed"></a><a name="fixed"></a>  fixed  
 Especifica que un número de punto flotante se muestre en notación de decimal fijo.  
  
```  
ios_base& fixed(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 **fixed** es la notación de presentación predeterminada para números de punto flotante. [scientific](../standard-library/ios-functions.md#scientific) hace que los números de punto flotante se muestren con notación científica.  
  
 El manipulador llama eficazmente a * str.*[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::fixed`, **ios_base::floatfield**) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_fixed.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 1.1F;  
  
   cout << i << endl;   // fixed is the default  
   cout << scientific << i << endl;  
   cout.precision( 1 );  
   cout << fixed << i << endl;  
}  
```  
  
```Output  
1.1  
1.100000e+000  
1.1  
```  
  
##  <a name="a-namehexa--hex"></a><a name="hex"></a>  hex  
 Especifica que las variables de entero aparezcan en notación de base 16.  
  
```  
ios_base& hex(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las variables de entero se muestran en notación de base 10. [dec](../standard-library/ios-functions.md#dec) y [oct](../standard-library/ios-functions.md#oct) también cambian la forma en que aparecen las variables de entero.  
  
 El manipulador llama eficazmente a ` str`**.**[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::hex`, **ios_base::basefield**) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [dec](../standard-library/ios-functions.md#dec) para obtener un ejemplo de cómo usar **hex**.  
  
##  <a name="a-nameinternala--internal"></a><a name="internal"></a>  internal  
 Hace que el signo de un número esté justificado a la izquierda y el número se alinee a la derecha.  
  
```  
ios_base& internal(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva ` str`.  
  
### <a name="remarks"></a>Comentarios  
 [showpos](../standard-library/ios-functions.md#showpos) hace que se muestre el signo de los números positivos.  
  
 El manipulador llama eficazmente a ` str`. [setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::internal](../standard-library/ios-base-class.md#ios_base__fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#ios_base__fmtflags)) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_internal.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
  
int main( void )   
{  
   using namespace std;  
   float i = -123.456F;  
   cout.fill( '.' );  
   cout << setw( 10 ) << i << endl;  
   cout << setw( 10 ) << internal << i << endl;  
}  
```  
  
```Output  
..-123.456  
-..123.456  
```  
  
##  <a name="a-namelefta--left"></a><a name="left"></a>  left  
 Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen izquierdo.  
  
```  
ios_base& left(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::left`, **ios_base::adjustfield**) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_left.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout.width( 20 );   
   cout << f1 << endl;  
   cout << left << f1 << endl;  
}  
```  
  
```Output  
                   5  
5  
```  
  
##  <a name="a-namenoboolalphaa--noboolalpha"></a><a name="noboolalpha"></a>  noboolalpha  
 Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como 1 o 0 en el flujo.  
  
```  
ios_base& noboolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `noboolalpha` está en vigor.  
  
 `noboolalpha` llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::boolalpha`) y, después, devuelve ` str`.  
  
 [boolalpha](../standard-library/ios-functions.md#boolalpha) invierte el efecto de `noboolalpha`.  
  
### <a name="example"></a>Ejemplo  
  Vea [boolalpha](../standard-library/ios-functions.md#boolalpha) para obtener un ejemplo que usa `noboolalpha`.  
  
##  <a name="a-namenoshowbasea--noshowbase"></a><a name="noshowbase"></a>  noshowbase  
 Desactiva la opción que indica la base notacional en que se muestra un número.  
  
```  
ios_base& noshowbase(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 La opción `noshowbase` está activada de manera predeterminada. Use [showbase](../standard-library/ios-functions.md#showbase) para indicar la base notacional de los números.  
  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showbase`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [showbase](../standard-library/ios-functions.md#showbase) para obtener un ejemplo de cómo usar `noshowbase`.  
  
##  <a name="a-namenoshowpointa--noshowpoint"></a><a name="noshowpoint"></a>  noshowpoint  
 Muestra solo la parte de número entero en los números de punto flotante cuya parte fraccionaria es cero.  
  
```  
ios_base& noshowpoint(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 `noshowpoint` está activado de forma predeterminada; use [showpoint](../standard-library/ios-functions.md#showpoint) y [precision](../standard-library/ios-base-class.md#ios_base__precision) para mostrar ceros después del punto decimal.  
  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showpoint`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_noshowpoint.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.000;  
   cout << f1 << endl;   // noshowpoint is default  
   cout.precision( 4 );  
   cout << showpoint << f1 << endl;  
   cout << noshowpoint << f1 << endl;  
}  
```  
  
```Output  
5  
5.000  
5  
```  
  
##  <a name="a-namenoshowposa--noshowpos"></a><a name="noshowpos"></a>  noshowpos  
 Hace que los números positivos no tengan signo explícito.  
  
```  
ios_base& noshowpos(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 La opción `noshowpos` está activada de manera predeterminada.  
  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showps`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [showpos](../standard-library/ios-functions.md#showpos) para obtener un ejemplo que usa `noshowpos`.  
  
##  <a name="a-namenoskipwsa--noskipws"></a><a name="noskipws"></a>  noskipws  
 Hace que el flujo de entrada lea los espacios.  
  
```  
ios_base& noskipws(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, [skipws](../standard-library/ios-functions.md#skipws) está en vigor. Cuando se lee un espacio en el flujo de entrada, señala el final del búfer.  
  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::skipws`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_noskipws.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
  
int main() {  
   using namespace std;     
   string s1, s2, s3;  
   cout << "Enter three strings: ";  
   cin >> noskipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;     
}  
```  
  
##  <a name="a-namenounitbufa--nounitbuf"></a><a name="nounitbuf"></a>  nounitbuf  
 Hace que la salida se almacene en búfer y se procese cuando el búfer esté lleno.  
  
```  
ios_base& nounitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 [unitbuf](../standard-library/ios-functions.md#unitbuf) hace que el búfer se procese cuando no está vacío.  
  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::unitbuf`) y, después, devuelve ` str`.  
  
##  <a name="a-namenouppercasea--nouppercase"></a><a name="nouppercase"></a>  nouppercase  
 Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en minúscula.  
  
```  
ios_base& nouppercase(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador llama eficazmente a ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::uppercase`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [uppercase](../standard-library/ios-functions.md#uppercase) para obtener un ejemplo que usa `nouppercase`.  
  
##  <a name="a-nameocta--oct"></a><a name="oct"></a>  oct  
 Especifica que las variables de entero aparezcan en notación de base 8.  
  
```  
ios_base& oct(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las variables de entero se muestran en notación de base 10. [dec](../standard-library/ios-functions.md#dec) y [hex](../standard-library/ios-functions.md#hex) también cambian la forma en que aparecen las variables de entero.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::oct`, `ios_base::basefield`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [dec](../standard-library/ios-functions.md#dec) para obtener un ejemplo de cómo usar **oct**.  
  
##  <a name="a-namerighta--right"></a><a name="right"></a>  right  
 Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen derecho.  
  
```  
ios_base& right(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 [left](../standard-library/ios-functions.md#left) también modifica la justificación del texto.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::right`, `ios_base::adjustfield`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_right.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << left << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << right << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
}  
```  
  
```Output  
5  
                   5  
5                     
5                     
                   5  
                   5  
```  
  
##  <a name="a-namescientifica--scientific"></a><a name="scientific"></a>  scientific  
 Hace que los números de punto flotante se muestren con notación científica.  
  
```  
ios_base& scientific(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la notación [fixed](../standard-library/ios-functions.md#fixed) está en vigor para los números de punto flotante.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::scientific`, `ios_base::floatfield`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_scientific.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 100.23F;  
  
   cout << i << endl;  
   cout << scientific << i << endl;  
}  
```  
  
```Output  
100.23  
1.002300e+002  
```  
  
##  <a name="a-nameshowbasea--showbase"></a><a name="showbase"></a>  showbase  
 Indica la base notacional en que se muestra un número.  
  
```  
ios_base& showbase(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 La base notacional de un número puede cambiarse por [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) o [hex](../standard-library/ios-functions.md#hex).  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showbase`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_showbase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int j = 100;  
  
   cout << showbase << j << endl;   // dec is default  
   cout << hex << j << showbase << endl;  
   cout << oct << j << showbase << endl;  
  
   cout << dec << j << noshowbase << endl;  
   cout << hex << j << noshowbase << endl;  
   cout << oct << j << noshowbase << endl;  
}  
```  
  
```Output  
100  
0x64  
0144  
100  
64  
144  
```  
  
##  <a name="a-nameshowpointa--showpoint"></a><a name="showpoint"></a>  showpoint  
 Muestra la parte de número entero de un número de punto flotante y los dígitos que hay a la derecha del separador decimal, incluso cuando la parte fraccionaria es cero.  
  
```  
ios_base& showpoint(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, [noshowpoint](../standard-library/ios-functions.md#noshowpoint) está en vigor.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showpoint`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [noshowpoint](../standard-library/ios-functions.md#noshowpoint) para obtener un ejemplo que usa `showpoint`.  
  
##  <a name="a-nameshowposa--showpos"></a><a name="showpos"></a>  showpos  
 Hace que los números positivos tengan signo explícito.  
  
```  
ios_base& showpos(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 [noshowpos](../standard-library/ios-functions.md#noshowpos) es el valor predeterminado.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showpos`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_showpos.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 1;  
  
   cout << noshowpos << i << endl;   // noshowpos is default  
   cout << showpos << i << endl;  
}  
```  
  
```Output  
1  
+1  
```  
  
##  <a name="a-nameskipwsa--skipws"></a><a name="skipws"></a>  skipws  
 Hace que el flujo de entrada no lea los espacios.  
  
```  
ios_base& skipws(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva _ *Str*.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `skipws` está en vigor. [noskipws](../standard-library/ios-functions.md#noskipws) hace que se lean los espacios del flujo de entrada.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::skipws`) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   char s1, s2, s3;  
   cout << "Enter three characters: ";  
   cin >> skipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;  
}  
```  
  
```Output  
  
1 2 3  
  
```  
  
```Output  
  
      1 2 3.1.  
.2.  
.3.  
```  
  
##  <a name="a-nameunitbufa--unitbuf"></a><a name="unitbuf"></a>  unitbuf  
 Hace que la salida se procese cuando el búfer no está lleno.  
  
```  
ios_base& unitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva ` str`.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que `endl` también vacía el búfer.  
  
 [nounitbuf](../standard-library/ios-functions.md#nounitbuf) está en vigor de forma predeterminada.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#ios_base__fmtflags)) y, después, devuelve ` str`.  
  
##  <a name="a-nameuppercasea--uppercase"></a><a name="uppercase"></a>  uppercase  
 Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en mayúscula.  
  
```  
ios_base& uppercase(ios_base& str);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto del que se deriva ` str`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, [nouppercase](../standard-library/ios-functions.md#nouppercase) está en vigor.  
  
 El manipulador llama eficazmente a ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#ios_base__fmtflags)) y, después, devuelve ` str`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// ios_uppercase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )   
{  
   using namespace std;  
  
   double i = 1.23e100;  
   cout << i << endl;  
   cout << uppercase << i << endl;  
  
   int j = 10;  
   cout << hex << nouppercase << j << endl;  
   cout << hex << uppercase << j << endl;  
}  
```  
  
```Output  
1.23e+100  
1.23E+100  
a  
A  
```  
  
## <a name="see-also"></a>Vea también  
 [\<ios>](../standard-library/ios.md)


