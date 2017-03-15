---
title: "Operadores de desplazamiento a la izquierda y a la derecha (&gt;&gt; y &lt;&lt;) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "<<"
  - ">>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<< (operador), con objetos específicos"
  - ">> (operador)"
  - "operadores de desplazamiento bit a bit"
  - "operadores de desplazamiento a la izquierda"
  - "operadores [C++], desplazamiento"
  - "operadores de desplazamiento a la derecha"
  - "operadores de desplazamiento"
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de desplazamiento a la izquierda y a la derecha (&gt;&gt; y &lt;&lt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores de desplazamiento bit a bit son el operador de desplazamiento a la derecha \(`>>`\), que mueve los bits de `shift_expression` a la derecha, y el operador de desplazamiento a la izquierda \(`<<`\), que mueve los bits de `shift_expression` a la izquierda.  <sup>1</sup>  
  
## Sintaxis  
  
```  
  
        shift-expression << additive-expression  
shift-expression >> additive-expression  
```  
  
## Comentarios  
  
> [!IMPORTANT]
>  Las descripciones y los ejemplos siguientes son válidos en Windows para las arquitecturas X86 y x64.  La implementación de los operadores de desplazamiento a la izquierda y desplazamiento a la derecha es muy diferente en los dispositivos Windows RT para ARM.  Para obtener más información, consulte la sección "Operadores de desplazamiento" de la entrada de blog [Hello ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx).  
  
## Desplazamientos a la izquierda  
 El operador de desplazamiento a la izquierda hace que los bits de `shift-expression` se desplacen hacia la izquierda el número de posiciones especificado por `additive-expression`.  Las posiciones de bits que quedan vacantes debido a la operación de desplazamiento se rellenan con ceros.  Un desplazamiento a la izquierda es un desplazamiento lógico \(los bits que se desplazan más allá del final se descartan, incluido el bit de signo\).  Para obtener más información sobre los tipos de desplazamiento bit a bit, consulte [Desplazamientos bit a bit](http://es.wikipedia.org/wiki/Operador_a_nivel_de_bits#Desplazamientos_de_bits).  
  
 En el ejemplo siguiente se muestran operaciones de desplazamiento a la izquierda con números sin signo.  El ejemplo muestra lo que ocurre con los bits representando el valor como un bitset.  Para obtener más información, consulte [bitset \(Clase\)](../standard-library/bitset-class.md).  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 Si desplaza a la izquierda un número con signo de modo que el bit de signo se vea afectado, el resultado es indefinido.  En el ejemplo siguiente se muestra lo que ocurre en Visual C\+\+ cuando un 1 bit se desplaza a la izquierda hasta la posición del bit de signo.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## Desplazamientos a la derecha  
 El operador de desplazamiento a la derecha hace que el patrón de bits de `shift-expression` se desplace hacia la derecha el número de posiciones especificado por `additive-expression`.  En el caso de números sin signo, las posiciones de bits que quedan vacantes debido a la operación de desplazamiento se rellenan con ceros.  Si se trata de números con signo, el bit de signo se emplea para rellenar las posiciones de bits vacantes.  Es decir, si el número es positivo se usa 0 y si el número es negativo se usa 1.  
  
> [!IMPORTANT]
>  El resultado de un desplazamiento a la derecha de un número negativo con signo depende de la implementación.  Aunque Visual C\+\+ usa el bit de signo para rellenar las posiciones de bits vacantes, no hay ninguna garantía de que otras implementaciones también lo hagan.  
  
 En este ejemplo se muestran operaciones de desplazamiento a la derecha que usan números sin signo:  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 En el ejemplo siguiente se muestran operaciones de desplazamiento a la derecha con números positivos con signo.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 En el ejemplo siguiente se muestran operaciones de desplazamiento a la derecha con enteros negativos con signo.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## Desplazamientos y promociones  
 Las expresiones especificadas a ambos lados de un operador de desplazamiento deben ser de tipos enteros.  Las promociones de enteros se realizan según las reglas que se describen en [Promociones de enteros](../misc/integral-promotions.md).  El tipo del resultado es el mismo que el tipo de `shift-expression` que se ha promovido.  
  
 En el ejemplo siguiente, una variable de tipo `char` se promueve a `int`.  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;  // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;   // int  
}  
```  
  
## Detalles adicionales  
 El resultado de una operación de desplazamiento es indefinido si `additive-expression` es negativo o si `additive-expression` es mayor o igual que el número de bits de `shift-expression` \(que se ha promovido\).  No se realiza ninguna operación de desplazamiento si `additive-expression` es 0.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## Notas al pie  
 1 A continuación se muestra la descripción de los operadores de desplazamiento en la especificación ISO de C\+\+ \(INCITS\/ISO\/IEC 14882\-2011 \[2012\]\), secciones 5.8.2 y 5.8.3.  
  
 El valor de `E1 << E2` es `E1` desplazado a la izquierda `E2` posiciones de bits; los bits vacantes se rellenan con ceros.  Si `E1` tiene un tipo sin signo, el valor resultante es `E1 × 2`<sup>E2</sup>, reduciendo cada módulo en uno más que el valor máximo que se puede representar en el tipo del resultado.  De lo contrario, si `E1` tiene un tipo con signo y un valor no negativo, y `E1 × 2`<sup>E2</sup> se puede representar en el tipo sin signo correspondiente del tipo del resultado, ese valor, convertido al tipo del resultado, es el valor resultante; de lo contrario, el comportamiento es indefinido.  
  
 El valor de `E1 >> E2` es `E1` desplazado a la derecha `E2` posiciones de bits.  Si `E1` tiene un tipo sin signo o si `E1` tiene un tipo con signo y un valor no negativo, el valor del resultado es la parte entera del cociente de `E1/2`<sup>E2</sup>.  Si `E1` tiene un tipo con signo y un valor negativo, el valor resultante está definido por la implementación.  
  
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)