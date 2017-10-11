---
title: Const (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- const_cpp
dev_langs:
- C++
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 8a6a238f28ec8f84cd127b4af88a84edb26506ee
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="const-c"></a>const (C++)
Cuando se modifica una declaración de datos, el **const** palabra clave especifica que el objeto o la variable no es modificable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>valores const  
 El **const** palabra clave especifica que el valor de una variable es constante e indica al compilador que evite que el programador lo modifique.  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 En C++, puede utilizar el **const** palabra clave en lugar de la [#define](../preprocessor/hash-define-directive-c-cpp.md) directiva de preprocesador para definir valores constantes. Los valores definidos con **const** están sujetos a la comprobación de tipos y puede usarse en lugar de expresiones constantes. En C++, puede especificar el tamaño de una matriz con un **const** variable como se indica a continuación:  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 En C, los valores constantes tienen la vinculación externa como valor predeterminado, por lo que solo pueden aparecer en los archivos de código fuente. En C++, los valores constantes tienen la vinculación interna como valor predeterminado, que permite que aparezcan en los archivos de encabezado.  
  
 El **const** palabra clave puede utilizarse en declaraciones de puntero.  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Un puntero a una variable declarada como **const** puede asignarse únicamente a un puntero que también se declara como **const**.  
  
```  
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
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Se puede llamar a funciones miembro de constante o que no son de constante para un objeto que no es constante. También puede sobrecargar una función miembro mediante la **const** palabra clave; Esto permite que una versión diferente de la función que se llamará para objetos constantes y.  
  
 No se puede declarar constructores o destructores con el **const** palabra clave.  
  
## <a name="const-member-functions"></a>funciones miembro const  
 Declarar una función miembro con el **const** palabra clave especifica que la función es una función de "solo lectura" que no modifica el objeto para el que se llama. Una función miembro constante no se puede modificar a los miembros de datos no estáticos ni llamar a funciones que no son constantes cualquier miembro. Para declarar una función miembro constante, coloque el **const** palabra clave después del paréntesis de cierre de la lista de argumentos. El **const** palabra clave es necesaria en la declaración y la definición.  
  
```  
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
  
```  
const int i = 2;  
```  
  
 A continuación, esta variable se puede utilizar en otro módulo como sigue:  
  
```  
extern const int i;  
```  
  
 Pero si desea para obtener el mismo comportamiento en C++, debe declarar la **const** variable como:  
  
```  
extern const int i = 2;  
```  
  
 Si desea declarar una variable `extern` en un archivo de código fuente de C++ para el uso en un archivo de código fuente de C, utilice:  
  
```  
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
