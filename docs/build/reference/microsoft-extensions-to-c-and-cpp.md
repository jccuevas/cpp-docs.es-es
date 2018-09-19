---
title: Extensiones de Microsoft para C y C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7de81d7611715e906b69f5546fafbcefa3252d64
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722480"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Extensiones de Microsoft para C y C++

Visual C++ extiende los estándares ANSI C y ANSI C++ de la forma siguiente.

## <a name="keywords"></a>Palabras clave

Se han agregado varias palabras clave. En la lista [palabras clave](../../cpp/keywords-cpp.md), las palabras clave que tienen dos subrayados iniciales son extensiones de Visual C++.

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>Fuera de la definición de clase de miembros de tipo entero (o enum) estáticos y constantes

En el estándar (**/Za**), debe realizar una definición de la clase para los miembros de datos, como se muestra aquí:

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

En **/Ze**, la definición de la clase es opcional para los miembros de datos de static, const integral y const enum. Solamente los miembros enteros y de enumeración de tipo static y const pueden tener inicializadores en una clase; la expresión de inicialización debe ser una expresión de constante.

Para evitar errores cuando una definición de la clase se proporciona en un encabezado de archivo y el archivo de encabezado se incluye en varios archivos de origen, use [selectany](../../cpp/selectany.md). Por ejemplo:

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>Conversiones

El compilador de C y el de C++ admiten estos tipos de conversiones no ANSI:

- Conversiones no ANSI para generar valores L. Por ejemplo:

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > Esta extensión solo está disponible en el lenguaje C. Puede utilizar el siguiente formato estándar ANSI C en el código de C++ para modificar un puntero como si fuera un puntero a un tipo diferente.

   El ejemplo anterior podría modificarse de la forma siguiente para adaptarlo al estándar ANSI C.

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- Conversiones no ANSI de un puntero de función en un puntero de datos. Por ejemplo:

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   Para realizar la misma conversión y mantener también la compatibilidad con ANSI, puede convertir el puntero de función en `uintptr_t` antes de convertirlo en un puntero de datos:

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>Listas de argumentos de longitud variable

El compilador de C++ y el de C admiten un declarador de función que especifica un número de argumentos variable, seguido de una definición de función que proporciona un tipo en su lugar:

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>Comentarios de una línea

El compilador de C acepta comentarios en una sola línea, que se introducen mediante dos caracteres de barra diagonal (//):

```C
// This is a single-line comment.
```

## <a name="scope"></a>Ámbito

El compilador de C acepta las siguientes características relacionadas con el ámbito.

- Redefiniciones de elementos extern como static:

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- Uso de redefiniciones de typedef sin efecto dentro del mismo ámbito:

   ```C
   typedef int INT;
   typedef int INT;
   ```

- Los declaradores de función tienen ámbito de archivo:

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- Uso de las variables de ámbito de bloque que se inicializan mediante expresiones no constantes:

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>Definiciones y declaraciones de datos

El compilador de C admite las siguientes características de declaración y definición de datos.

- Constantes de caracteres y cadenas mezcladas en un inicializador:

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- Campos de bit que tienen tipos base distinto **int sin signo** o **firmado int**.

- Declaradores que no tienen un tipo:

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- Matrices sin tamaño como último campo de estructuras y uniones:

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- Estructuras sin nombre (anónimas):

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- Uniones sin nombre (anónimas):

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- Miembros sin nombre:

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>Funciones intrínsecas de punto flotante

Ambos x86 el compilador de C++ y C admiten insertados, generación de la `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, y `tan` funciones cuando **/Oi** se especifica. Para el compilador de C, la conformidad con ANSI se pierde cuando se utilizan estas funciones intrínsecas, puesto que no definen la variable `errno`.

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Pasar un parámetro de puntero no const a una función que espera una referencia a un parámetro de puntero const

Esto es una extensión de C++. Este código se compilará con **/Ze**:

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646. H no habilitado

En **/Ze**, debe incluir iso646.h si desea usar formas de texto de los operadores siguientes:

- && (and)

- &= (and_eq)

- & (bitand)

- &#124;(bitor)

- ~ (compl)

- ! (not)

- != (not_eq)

- &#124;&#124;(o)

- &#124;= (or_eq)

- ^ (xor)

- ^= (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Dirección del literal de cadena tiene tipo const char [], no const char (*)]

El siguiente ejemplo escribirá `char const (*)[4]` en **/Za**, pero `char const [4]` en **/Ze**.

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>Vea también

- [/Za, /Ze (Deshabilitar extensiones de lenguaje)](../../build/reference/za-ze-disable-language-extensions.md)
- [Opciones del compilador](../../build/reference/compiler-options.md)
- [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
