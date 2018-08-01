---
title: Const (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cpp
dev_langs:
- C++
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73e030ede8305db4ea05826f0ce7704420ac0400
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403406"
---
# <a name="const-c"></a>const (C++)
Al modificar una declaración de datos, el **const** palabra clave especifica que el objeto o variable no es modificable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>valores const  
 El **const** palabra clave especifica que el valor de una variable es constante e indica al compilador que evite que el programador lo modifique.  
  
```cpp 
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 En C++, puede usar el **const** palabra clave en lugar de la [#define](../preprocessor/hash-define-directive-c-cpp.md) directiva de preprocesador para definir valores constantes. Los valores definidos con **const** están sujetos a la comprobación de tipo y puede usarse en lugar de expresiones constantes. En C++, puede especificar el tamaño de una matriz con un **const** variable como sigue:  
  
```cpp 
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 En C, los valores constantes tienen la vinculación externa como valor predeterminado, por lo que solo pueden aparecer en los archivos de código fuente. En C++, los valores constantes tienen la vinculación interna como valor predeterminado, que permite que aparezcan en los archivos de encabezado.  
  
 El **const** palabra clave puede utilizarse en declaraciones de puntero.  
  
```cpp 
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Un puntero a una variable declarada como **const** pueden asignarse solo a un puntero que también se declara como **const**.  
  
```cpp 
// constant_values4.cpp  
#include <stdio.h>  
int main() {  
   const char *mybuf = "test";  
   char *yourbuf = "test2";  
   printf_s("%s\n", mybuf);  
  
   const char *bptr = mybuf;   // Pointer to constant data  
   printf_s("%s\n", bptr);  
  
   // *bptr = 'a';   // Error  
}  
```  
  
 Puede utilizar punteros a datos constantes como parámetros de función para evitar que la función modifique un parámetro pasado a través de un puntero.  
  
 Para los objetos que se declaran como **const**, miembro de constante solo se puede invocar funciones. Esto garantiza que el objeto constante nunca se modifique.  
  
```cpp 
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Se puede llamar a funciones miembro de constante o que no son de constante para un objeto que no es constante. También puede sobrecargar una función miembro mediante el **const** palabra clave; Esto permite que una versión diferente de la función que se llamará para constantes y los objetos.  
  
 No se puede declarar constructores o destructores con el **const** palabra clave.  
  
## <a name="const-member-functions"></a>funciones miembro const  
 Declarar una función miembro con el **const** palabra clave especifica que la función es una función de "solo lectura" que no modifica el objeto para el que se llama. Una función miembro constante no puede modificar a los miembros de datos no estáticos ni llamar a cualquier miembro de las funciones que no sean constantes. Para declarar una función miembro constante, coloque el **const** palabra clave después del paréntesis de cierre de la lista de argumentos. El **const** palabra clave es necesaria en la declaración y la definición.  
  
```cpp 
// constant_member_function.cpp  
class Date  
{  
public:  
   Date( int mn, int dy, int yr );  
   int getMonth() const;     // A read-only function  
   void setMonth( int mn );   // A write function; can't be const  
private:  
   int month;  
};  
  
int Date::getMonth() const  
{  
   return month;        // Doesn't modify anything  
}  
void Date::setMonth( int mn )  
{  
   month = mn;          // Modifies data member  
}  
int main()  
{  
   Date MyDate( 7, 4, 1998 );  
   const Date BirthDate( 1, 18, 1953 );  
   MyDate.setMonth( 4 );    // Okay  
   BirthDate.getMonth();    // Okay  
   BirthDate.setMonth( 4 ); // C2662 Error  
}  
```  
  
## <a name="c-and-c-const-differences"></a>Diferencias de const en C y C++  
 Cuando se declara una variable como **const** en un archivo de código fuente de C, lo hace como:  
  
```cpp 
const int i = 2;  
```  
  
 A continuación, esta variable se puede utilizar en otro módulo como sigue:  
  
```cpp 
extern const int i;  
```  
  
 Pero para obtener el mismo comportamiento en C++, no se debe declarar la **const** variable como:  
  
```cpp 
extern const int i = 2;  
```  
  
 Si desea declarar una **extern** variable en un archivo de código fuente de C++ para su uso en un archivo de código fuente de C, use:  
  
```cpp 
extern "C" const int x=10;  
```  
  
 para evitar que el compilador de C++ elimine nombres.  
  
## <a name="remarks"></a>Comentarios  
 Al seguir la lista de parámetros de una función miembro, el **const** palabra clave especifica que la función no modifica el objeto para el que se invoca.  
  
 Para obtener más información sobre **const**, vea los temas siguientes:  
    
-   [Punteros const y volatile](../cpp/const-and-volatile-pointers.md)  
  
-   [Calificadores de tipo (referencia del lenguaje C)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)