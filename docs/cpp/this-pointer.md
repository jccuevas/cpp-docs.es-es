---
title: this (puntero) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- this_cpp
dev_langs:
- C++
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 86ccf50a089b1497bdc166ee9367215dc59b3ca1
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="this-pointer"></a>this (Puntero)
El **esto** puntero es un puntero accesible únicamente dentro de las funciones miembro no estáticas de una **clase**, `struct`, o **union** tipo. Señala al objeto para el que se llama a la función miembro. Las funciones miembro estáticas no tienen un **esto** puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      this   
this->member-identifier  
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto **esto** puntero no es parte del propio objeto; no se refleja en el resultado de una `sizeof` instrucción en el objeto. En su lugar, cuando se llama a una función miembro no estática para un objeto, el compilador pasa la dirección del objeto como un argumento oculto a la función. Por ejemplo, la siguiente llamada de función:  
  
```  
myDate.setMonth( 3 );  
```  
  
 se puede interpretar de esta manera:  
  
```  
setMonth( &myDate, 3 );  
```  
  
 La dirección del objeto está disponible en la función miembro como el **esto** puntero. La mayoría de los usos de **esto** son implícitas. Es válido, aunque es innecesario, utilizar explícitamente **esto** cuando se hace referencia a los miembros de la clase. Por ejemplo:  
  
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
  
 El **esto** puntero también se utiliza para protegerse de la referencia a sí misma:  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  Dado que la **esto** puntero no es modificable, las asignaciones a **esto** no se permiten. Implementaciones anteriores de C++ permitían las asignaciones a **esto**.  
  
 En ocasiones, el **esto** puntero se usa directamente, por ejemplo, para manipular los datos autorreferencia las estructuras, donde se requiere la dirección del objeto actual.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
my buffer  
your buffer  
```  
  
## <a name="type-of-the-this-pointer"></a>Tipo del puntero this  
 El **esto** se puede modificar el tipo de puntero en la declaración de función por la **const** y `volatile` palabras clave. Para declarar una función con los atributos de una o más de estas palabras clave, agregue las palabras clave después de la lista de argumentos de la función.  
  
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
  
 El código anterior declara una función miembro, `X`, en el que el **esto** puntero se trata como un **const** puntero a un **const** objeto. Combinaciones de *cv-mod-list* opciones pueden utilizarse, pero estas modifican siempre el objeto al que señala **esto**, no el **esto** propio puntero. Por lo tanto, la declaración siguiente declara la función `X`; el **esto** puntero es un **const** puntero a un **const** objeto:  
  
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
  
 El tipo de **esto** en un miembro de la función se describe mediante la sintaxis siguiente, donde *cv-qualifier-list* se determina a partir del declarador de funciones miembro y puede ser **const**o **volátiles** (o ambos), y *tipo de clase* es el nombre de la clase:  
  
 *tipo de clase [cv-qualifier-list]* ** \* const esto  **  
  
 En otras palabras, **esto** siempre es un puntero const; no se puede reasignar.  El **const** o `volatile` calificadores utilizados en la declaración de función miembro se aplican a la instancia de clase que señala **esto** en el ámbito de esa función.  
  
 En la tabla siguiente se explica más detalladamente el funcionamiento de estos modificadores.  
  
### <a name="semantics-of-this-modifiers"></a>Semántica de los modificadores de this  
  
|Modificador|Significado|  
|--------------|-------------|  
|**const**|No se puede cambiar los datos de miembro; no se puede llamar a funciones de miembro que no son **const**.|  
|`volatile`|Los datos de miembro se cargan desde la memoria cada vez que se obtiene acceso; deshabilita ciertas optimizaciones.|  
  
 Es un error pasar un **const** objeto a una función miembro que no sea **const**. De igual forma, es un error pasar un objeto `volatile` a una función miembro que no sea `volatile`.  
  
 Las funciones miembro declaradas como **const** no se puede cambiar los datos de miembros: en dichas funciones, la **esto** puntero es un puntero a un **const** objeto.  
  
> [!NOTE]
>  Constructores y destructores no pueden declararse como **const** o `volatile`. Sin embargo, pueden ser se invoca en **const** o `volatile` objetos.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 
