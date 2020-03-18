---
title: Funciones de &lt;locale&gt;
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 3c5d81aecb5e78a8fd3c3f32da82f6048ae4fac8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425572"
---
# <a name="ltlocalegt-functions"></a>Funciones de &lt;locale&gt;

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a>  has_facet

Comprueba si una faceta determinada se almacena en una configuración regional especificada.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parámetros

\ *Loc*
Configuración regional en la que se va a comprobar la presencia de una faceta.

### <a name="return-value"></a>Valor devuelto

**True** si la configuración regional tiene la faceta que se busca; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla es útil para comprobar si se enumeran facetas no obligatorias en una configuración regional antes de llamar a `use_facet` para evitar la excepción que se produciría si no estuvieran presentes.

### <a name="example"></a>Ejemplo

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a>  isalnum

Comprueba si un elemento de una configuración regional es un carácter alfabético o numérico.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento alfanumérico que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento alfanumérico que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es alfanumérico; en caso contrario, **False**.

### <a name="example"></a>Ejemplo

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a>  isalpha

Comprueba si un elemento de una configuración regional es un carácter alfabético.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento alfabético que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es alfabético; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Alpha**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a>  iscntrl

Comprueba si un elemento de una configuración regional es un carácter de control.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter de control; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Ctrl**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a>  isdigit

Comprueba si un elemento de una configuración regional es un carácter numérico.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter numérico; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **digit**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a>  isgraph

Comprueba si un elemento de una configuración regional es un carácter alfabético o un signo de puntuación.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter alfanumérico o de puntuación; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Graph**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a>  islower

Comprueba si un elemento de una configuración regional está en minúsculas.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**true** si el elemento probado es un carácter en minúscula; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Lower**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a>  isprint

Comprueba si un elemento de una configuración regional es un carácter imprimible.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter imprimible; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Print**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a>  ispunct

Comprueba si un elemento de una configuración regional es un carácter de signo de puntuación.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter de puntuación; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **punct**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a>  isspace

Comprueba si un elemento de una configuración regional es un carácter de espacio en blanco.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter de espacio en blanco; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Space**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a>  isupper

Comprueba si un elemento de una configuración regional está en mayúsculas.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**true** si el elemento probado es un carácter en mayúscula; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **Upper**, `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a>  isxdigit

Comprueba si un elemento de una configuración regional es un carácter usado para representar un número hexadecimal.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Elemento que se va a probar.

\ *Loc*
Configuración regional que contiene el elemento que se va a probar.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento probado es un carácter que se usa para representar un número hexadecimal; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [es](../standard-library/ctype-class.md#is)( **ctype**\< **CharType**>:: **xdigit**, `Ch`).

Los dígitos hexadecimales usan la base 16 para representar números, con los números del 0 al 9 y las letras de la A a la F sin distinción entre mayúsculas y minúsculas para representar los números decimales del 0 al 15.

### <a name="example"></a>Ejemplo

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a>  tolower

Pasa un carácter a minúsculas.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
El carácter que se va a convertir en minúscula.

\ *Loc*
Configuración regional que contiene el carácter que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Carácter convertido en minúscula.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [tolower](../standard-library/ctype-class.md#tolower)( `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a>  toupper

Pasa un carácter a mayúsculas.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parámetros

\ de *CH*
El carácter que se va a convertir en mayúscula.

\ *Loc*
Configuración regional que contiene el carácter que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Carácter convertido en mayúscula.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> > (`Loc`). [toupper](../standard-library/ctype-class.md#toupper)( `Ch`).

### <a name="example"></a>Ejemplo

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a>  use_facet

Devuelve una referencia a una faceta de un tipo especificado almacenado en una configuración regional.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parámetros

\ *Loc*
Configuración regional const que contiene el tipo de faceta al que se hace referencia.

### <a name="return-value"></a>Valor devuelto

Referencia a la faceta de la clase `Facet` contenida en la configuración regional del argumento.

### <a name="remarks"></a>Observaciones

La referencia a la faceta devuelta por la función de plantilla es válida mientras exista una copia de la configuración regional que la contiene. Si ese objeto de faceta de la clase `Facet` no aparece en la configuración regional del argumento, la función produce una excepción `bad_cast`.

### <a name="example"></a>Ejemplo

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>Consulte también

[\<locale>](../standard-library/locale.md)
