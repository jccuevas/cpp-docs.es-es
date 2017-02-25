---
title: "this (Puntero) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "this"
  - "this_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones miembro no estáticas"
  - "punteros, a instancia de clase"
  - "this (puntero)"
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# this (Puntero)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El puntero **this** es un puntero accesible solo dentro de las funciones miembro no estáticas de un tipo de **clase**, `struct` o de **unión**.  Señala al objeto para el que se llama a la función miembro.  Las funciones miembro estáticas no tienen un puntero **this**.  
  
## Sintaxis  
  
```  
  
        this   
this->member-identifier  
```  
  
## Comentarios  
 El puntero **this** de un objeto no forma parte del propio objeto; no se refleja en el resultado de una instrucción `sizeof` en el objeto.  En su lugar, cuando se llama a una función miembro no estática para un objeto, el compilador pasa la dirección del objeto como un argumento oculto a la función.  Por ejemplo, la siguiente llamada de función:  
  
```  
myDate.setMonth( 3 );  
```  
  
 se puede interpretar de esta manera:  
  
```  
setMonth( &myDate, 3 );  
```  
  
 La dirección del objeto está disponible desde la función miembro como el puntero **this**.  La mayoría de los usos de **this** son implícitos.  Es válido, aunque innecesario, utilizar explícitamente **this** cuando se hace referencia a los miembros de la clase.  Por ejemplo:  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 La expresión `*this` suele utilizarse para devolver el objeto actual desde una función miembro:  
  
```  
return *this;  
```  
  
 El puntero **this** también se utiliza para protegerse de la autorreferencia:  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  Dado que el puntero **this** no es modificable, no se permiten las asignaciones a **this**.  Implementaciones anteriores de C\+\+ permitían las asignaciones a **this**.  
  
 En ocasiones, el puntero **this** se utiliza directamente; por ejemplo, para manipular estructuras de datos que hacen referencia a sí mismas, donde se requiere la dirección del objeto actual.  
  
## Ejemplo  
  
```  
// this_pointer.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
class Buf   
{  
public:  
    Buf( char* szBuffer, size_t sizeOfBuffer );  
    Buf& operator=( const Buf & );  
    void Display() { cout << buffer << endl; }  
  
private:  
    char*   buffer;  
    size_t  sizeOfBuffer;  
};  
  
Buf::Buf( char* szBuffer, size_t sizeOfBuffer )  
{  
    sizeOfBuffer++; // account for a NULL terminator  
  
    buffer = new char[ sizeOfBuffer ];  
    if (buffer)  
    {  
        strcpy_s( buffer, sizeOfBuffer, szBuffer );  
        sizeOfBuffer = sizeOfBuffer;  
    }  
}  
  
Buf& Buf::operator=( const Buf &otherbuf )   
{  
    if( &otherbuf != this )   
    {  
        if (buffer)  
            delete [] buffer;  
  
        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;   
        buffer = new char[sizeOfBuffer];  
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );  
    }  
    return *this;  
}  
  
int main()  
{  
    Buf myBuf( "my buffer", 10 );  
    Buf yourBuf( "your buffer", 12 );  
  
    // Display 'my buffer'  
    myBuf.Display();  
  
    // assignment opperator  
    myBuf = yourBuf;  
  
    // Display 'your buffer'  
    myBuf.Display();  
}  
```  
  
  **my buffer**  
**your buffer**   
## Tipo del puntero this  
 El tipo de puntero **this** puede modificarse en la declaración de función mediante las palabras clave **const** y `volatile`.  Para declarar una función con los atributos de una o más de estas palabras clave, agregue las palabras clave después de la lista de argumentos de la función.  
  
 Considere este ejemplo:  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 El código anterior declara una función miembro, `X`, en la que el puntero **this** se trata como un puntero **const** a un objeto **const**.  Se pueden usar combinaciones de opciones de *cv\-mod\-list*, pero estas modifican siempre el objeto al que señala **this**, no el puntero **this** propiamente dicho.  Por consiguiente, en la declaración siguiente se declara la función `X`; el puntero **this** es un puntero **const** a un objeto **const**:  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 La sintaxis siguiente describe el tipo de **this** en una función miembro, donde *cv\-qualifier\-list* se determina a partir del declarador de funciones miembro y puede ser **const** o **volatile** \(o ambos\). *class\-type* es el nombre de la clase:  
  
 *\[cv\-qualifier\-list\] class\-type*  **\* const this**  
  
 Dicho de otro modo, **this** siempre es un puntero const; no se puede reasignar.  Los calificadores **const** o `volatile` que se usan en la declaración de función miembro se aplican a la instancia de clase a la que apunta **this** en el ámbito de dicha función.  
  
 En la tabla siguiente se explica más detalladamente el funcionamiento de estos modificadores.  
  
### Semántica de los modificadores de this  
  
|Modificador|Significado|  
|-----------------|-----------------|  
|**const**|No puede cambiar los datos de miembro; no puede llamar a funciones miembro que no sean **const**.|  
|`volatile`|Los datos de miembro se cargan desde la memoria cada vez que se obtiene acceso; deshabilita ciertas optimizaciones.|  
  
 Es un error pasar un objeto **const** a una función miembro que no sea **const**.  De igual forma, es un error pasar un objeto `volatile` a una función miembro que no sea `volatile`.  
  
 Las funciones miembro declaradas como **const** no pueden cambiar los datos de miembro \(en dichas funciones, el puntero **this** es un puntero a un objeto **const**\).  
  
> [!NOTE]
>  Los constructores y destructores no pueden declararse como **const** o `volatile`.  Pueden, sin embargo, invocarse en objetos **const** o `volatile`.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Tipo de puntero this](../misc/type-of-this-pointer.md)   
 [Coincidencia de argumentos y el puntero this](../misc/argument-matching-and-the-this-pointer.md)