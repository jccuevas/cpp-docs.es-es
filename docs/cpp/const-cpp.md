---
title: "const (C++) | Microsoft Docs"
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
  - "const_cpp"
  - "const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const (palabra clave) [C++]"
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se modifica una declaración de datos, la palabra clave **const** especifica que el objeto o la variable no se puede modificar.  
  
## Sintaxis  
  
```  
  
        const declaration ;  
member-function const ;  
```  
  
## valores const  
 La palabra clave **const** especifica que el valor de una variable es constante e indica al compilador que evite que el programador lo modifique.  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 En C\+\+, se puede utilizar la palabra clave **const** en lugar de la directiva de preprocesador [\#define](../preprocessor/hash-define-directive-c-cpp.md) para definir valores constantes.  Los valores definidos con **const** están sujetos a la comprobación de tipos y se pueden usar en lugar de expresiones constantes.  En C\+\+, puede especificar el tamaño de una matriz con una variable **const** de la forma siguiente:  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 En C, los valores constantes tienen la vinculación externa como valor predeterminado, por lo que solo pueden aparecer en los archivos de código fuente.  En C\+\+, los valores constantes tienen la vinculación interna como valor predeterminado, que permite que aparezcan en los archivos de encabezado.  
  
 La palabra clave **const** también se puede utilizar en las declaraciones de puntero.  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Un puntero a una variable declarada como **const** solo se puede asignar a un puntero que también se declare como **const**.  
  
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
  
 Para los objetos que se declaran como **const**, solo se puede llamar a las [funciones miembro de constante](../misc/constant-member-functions.md).  Esto garantiza que el objeto constante nunca se modifique.  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Se puede llamar a funciones miembro de constante o que no son de constante para un objeto que no es constante.  Una función miembro también se puede sobrecargar mediante la palabra clave **const**; esto permite que se llame a una versión diferente de la función para los objetos constantes y que no son constantes.  
  
 Los constructores o destructores no se pueden declarar con la palabra clave **const**.  
  
## funciones miembro const  
 Declarar una función miembro con la palabra clave **const** especifica que la función es una función de “solo lectura” que no modifica el objeto para el que se llama.  Una función miembro constante no puede modificar los miembros de datos no estáticos ni llamar a funciones miembro que no sean constantes. Para declarar una función miembro constante, coloque la palabra clave **const** después del paréntesis de cierre de la lista de argumentos.  La palabra clave **const** se requiere tanto en la declaración como en la definición.  
  
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
  
## Diferencias de const en C y C\+\+  
 Cuando se declara una variable como **const** en el archivo de código fuente de C, se hace de la forma siguiente:  
  
```  
const int i = 2;  
```  
  
 A continuación, esta variable se puede utilizar en otro módulo como sigue:  
  
```  
extern const int i;  
```  
  
 Pero si desea obtener el mismo comportamiento en C\+\+, debe declarar la variable **const** como:  
  
```  
extern const int i = 2;  
```  
  
 Si desea declarar una variable `extern` en un archivo de código fuente de C\+\+ para el uso en un archivo de código fuente de C, utilice:  
  
```  
extern "C" const int x=10;  
```  
  
 para evitar que el compilador de C\+\+ elimine nombres.  
  
## Comentarios  
 Cuando va después de la lista de parámetros de una función miembro, la palabra clave **const** especifica que la función no modifica el objeto para el que se invoca.  
  
 Para obtener más información sobre **const**, vea uno de los temas siguientes:  
  
-   [Valores constantes](../misc/constant-values.md)  
  
-   [Funciones miembro constantes](../misc/constant-member-functions.md)  
  
-   [Punteros const y volatile](../cpp/const-and-volatile-pointers.md)  
  
-   [Calificadores de tipo \(Referencia del lenguaje C\)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [\#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)