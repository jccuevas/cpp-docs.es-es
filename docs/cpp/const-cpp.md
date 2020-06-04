---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: cc1f117cc5f26edf9cd85461281b925c97fa5225
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180309"
---
# <a name="const-c"></a>const (C++)

Al modificar una declaración de datos, la palabra clave **const** especifica que el objeto o la variable no es modificable.

## <a name="syntax"></a>Sintaxis

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>valores const

La palabra clave **const** especifica que el valor de una variable es constante e indica al compilador que evite que el programador la modifique.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

En C++, puede utilizar la palabra clave **const** en lugar de la directiva de preprocesador [#define](../preprocessor/hash-define-directive-c-cpp.md) para definir valores constantes. Los valores definidos con **const** están sujetos a la comprobación de tipos y se pueden usar en lugar de expresiones constantes. En C++, puede especificar el tamaño de una matriz con una variable **const** de la siguiente manera:

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

En C, los valores constantes tienen la vinculación externa como valor predeterminado, por lo que solo pueden aparecer en los archivos de código fuente. En C++, los valores constantes tienen la vinculación interna como valor predeterminado, que permite que aparezcan en los archivos de encabezado.

La palabra clave **const** también se puede utilizar en declaraciones de puntero.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Un puntero a una variable declarada como **const** solo se puede asignar a un puntero que también se declara como **const**.

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

En el caso de los objetos que se declaran como **const**, solo puede llamar a funciones miembro de constante. Esto garantiza que el objeto constante nunca se modifique.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Se puede llamar a funciones miembro de constante o que no son de constante para un objeto que no es constante. También puede sobrecargar una función miembro mediante la palabra clave **const** ; Esto permite llamar a una versión diferente de la función para objetos constantes y no constantes.

No se pueden declarar constructores o destructores con la palabra clave **const** .

## <a name="const-member-functions"></a>funciones miembro const

La declaración de una función miembro con la palabra clave **const** especifica que la función es una función de "solo lectura" que no modifica el objeto para el que se llama. Una función miembro constante no puede modificar los miembros de datos no estáticos ni llamar a funciones miembro que no sean constantes. Para declarar una función miembro constante, coloque la palabra clave **const** después del paréntesis de cierre de la lista de argumentos. La palabra clave **const** se requiere en la declaración y en la definición.

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

## <a name="c-and-c-const-differences"></a>Diferencias de C++ C y const

Cuando se declara una variable como **const** en un archivo de código fuente de C, se hace así:

```cpp
const int i = 2;
```

A continuación, esta variable se puede utilizar en otro módulo como sigue:

```cpp
extern const int i;
```

Pero para obtener el mismo comportamiento en C++, debe declarar la variable **const** como:

```cpp
extern const int i = 2;
```

Si desea declarar una variable **extern** en un C++ archivo de código fuente para su uso en un archivo de código fuente de C, use:

```cpp
extern "C" const int x=10;
```

para evitar que el compilador de C++ elimine nombres.

## <a name="remarks"></a>Observaciones

Cuando se sigue la lista de parámetros de una función miembro, la palabra clave **const** especifica que la función no modifica el objeto para el que se invoca.

Para obtener más información sobre **const**, vea los temas siguientes:

- [Punteros const y volatile](../cpp/const-and-volatile-pointers.md)

- [Calificadores de tipo (referencia del lenguaje C)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
