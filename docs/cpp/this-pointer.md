---
title: Puntero this
description: El puntero this es un puntero generado por el compilador al objeto actual en funciones miembro no estáticas.
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518340"
---
# <a name="opno-locthis-pointer"></a>Puntero this

El puntero **this** es un puntero accesible únicamente dentro de las funciones miembro no estáticas de un tipo **class** , **struct** o **union** . Señala al objeto para el que se llama a la función miembro. Las funciones miembro estáticas no tienen un puntero **this** .

## <a name="syntax"></a>Sintaxis

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Notas

El puntero **this** de un objeto no forma parte del propio objeto. No se refleja en el resultado de una instrucción **sizeof** en el objeto. Cuando se llama a una función miembro no estática para un objeto, el compilador pasa la dirección del objeto a la función como un argumento oculto. Por ejemplo, la siguiente llamada de función:

```cpp
myDate.setMonth( 3 );
```

se puede interpretar como:

```cpp
setMonth( &myDate, 3 );
```

La dirección del objeto está disponible desde la función miembro como el puntero **this** . La mayoría de los usos de **this** puntero son implícitos. Aunque no es necesario, es legal usar una **this** explícita al hacer referencia a los miembros de la class. Por ejemplo:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

La expresión `*this` suele utilizarse para devolver el objeto actual desde una función miembro:

```cpp
return *this;
```

El puntero **this** también se usa para protegerse de la autoreferencia:

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Dado que el puntero **this** no es modificable, no se permiten las asignaciones al puntero **this** . Implementaciones anteriores de C++ asignación permitida para **this** .

En ocasiones, el puntero de **this** se utiliza directamente, por ejemplo, para manipular estructuras de datos autoreferencial, donde se requiere la dirección del objeto actual.

## <a name="example"></a>Ejemplo

```cpp
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

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-opno-locthis-pointer"></a>Tipo del puntero this

El tipo del puntero **this** se puede modificar en la declaración de la función por las palabras clave **const** y **volatile** . Para declarar una función que tenga cualquiera de estos atributos, agregue las palabras clave después de la lista de argumentos de la función.

Considere un ejemplo:

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

El código anterior declara una función miembro, `X`, en la que el puntero de **this** se trata como un puntero de **const** a un objeto de **const** . Se pueden utilizar combinaciones de opciones *CV-mod-List* , pero siempre modifican el objeto al que apunta el puntero **this** , no el propio puntero. La siguiente declaración declara la función `X`, donde el puntero **this** es un puntero **const** a un objeto **const** :

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

La sintaxis siguiente describe el tipo de **this** en una función miembro. La *lista CV-Qualifier-List* se determina a partir del declarador de la función miembro. Puede ser **const** o **volatile** (o ambos). *class-Type* es el nombre del class:

[*VC-Qualifier-List*] const *de\* de tipoclass* **this**

En otras palabras, el puntero **this** es siempre un puntero const. No se puede reasignar.  Los calificadores **const** o **volatile** utilizados en la declaración de función miembro se aplican a la instancia de class a la que apunta el puntero **this** , en el ámbito de esa función.

En la tabla siguiente se explica más detalladamente el funcionamiento de estos modificadores.

### <a name="semantics-of-opno-locthis-modifiers"></a>Semántica de los modificadores de this

|Modificador|Significado|
|--------------|-------------|
|**const**|No se pueden cambiar los datos de miembro; no se pueden invocar funciones miembro que no estén **const** .|
|**volatile**|Los datos de miembro se cargan desde la memoria cada vez que se accede a ellos. deshabilita ciertas optimizaciones.|

Es un error pasar un objeto de **const** a una función miembro que no está **const** .

Del mismo modo, también es un error pasar un objeto **volatile** a una función miembro que no está **volatile** .

Las funciones miembro declaradas como **const** no pueden cambiar los datos de miembro: en tales funciones, el puntero de **this** es un puntero a un objeto **const** .

> [!NOTE]
> Los constructores y destructores no se pueden declarar como **const** o **volatile** . Sin embargo, se pueden invocar en objetos **const** o **volatile** .

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)
