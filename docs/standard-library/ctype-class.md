---
title: ctype (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
dev_langs:
- C++
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49329d97343cfd210a93879961b0492454be9efa
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954778"
---
# <a name="ctype-class"></a>ctype (Clase)

Clase que proporciona una faceta que se emplea para clasificar los caracteres, pasar de mayúsculas a minúsculas y convertir entre el juego de caracteres nativo y el que usa la configuración regional.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parámetros

*CharType* tipo usado dentro de un programa para codificar los caracteres.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`. Se proporciona a los criterios de clasificación un tipo de máscara de bits anidado en el ctype_base de la clase base.

La biblioteca estándar de C++ define dos especializaciones explícitas de esta clase de plantilla:

- [ctype](../standard-library/ctype-char-class.md)< `char`>, una especialización explícita cuyas diferencias se describen por separado.

- **ctype**<`wchar_t`>, que trata los elementos como caracteres anchos.

Otras especializaciones de la clase de plantilla **ctype**\< **CharType**>:

- Convertir un valor ***ch*** typu `CharType` en un valor de tipo **char** con la expresión (`char`) **ch**.

- Convertir un valor ***bytes*** typu **char** en un valor de tipo `CharType` con la expresión **CharType** (**bytes**).

Todas las demás operaciones se realizan en **char** valores en la misma manera que la especialización explícita **ctype**<`char`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ctype](#ctype)|Constructor de objetos de clase `ctype` que actúan como facetas de configuración regional para los caracteres.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que describe un carácter usado por una configuración regional.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[do_is](#do_is)|Función virtual a la que se llama para comprobar si un carácter individual tiene un atributo determinado, o para clasificar los atributos de cada carácter de un intervalo y almacenarlos en una matriz.|
|[do_narrow](#do_narrow)|Una función virtual llamada para convertir un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo **char** en el carácter nativo establecido.|
|[do_scan_is](#do_scan_is)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que coincide con una máscara especificada.|
|[do_scan_not](#do_scan_not)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que no coincide con una máscara especificada.|
|[do_tolower](#do_tolower)|Función virtual a la que se llama para convertir a minúsculas un carácter o un intervalo de caracteres.|
|[do_toupper](#do_toupper)|Función virtual a la que se llama para convertir a mayúsculas un carácter o un intervalo de caracteres.|
|[do_widen](#do_widen)|Una función virtual llamada para convierte un carácter de tipo **char** en el juego en el carácter correspondiente de tipo de caracteres nativo `CharType` usado por una configuración regional.|
|[is](#is)|Comprueba si un carácter individual tiene un atributo determinado, o clasifica los atributos de cada carácter de un intervalo y los almacena en una matriz.|
|[narrow](#narrow)|Convierte un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo char del juego de caracteres nativo.|
|[scan_is](#scan_is)|Busca el primer carácter de un intervalo que coincide con una máscara especificada.|
|[scan_not](#scan_not)|Busca el primer carácter de un intervalo que no coincide con una máscara especificada.|
|[tolower](#tolower)|Convierte a minúsculas un carácter o un intervalo de caracteres.|
|[toupper](#toupper)|Convierte a mayúsculas un carácter o un intervalo de caracteres.|
|[widen](#widen)|Convierte un carácter de tipo **char** en el juego en el carácter correspondiente de tipo de caracteres nativo `CharType` usado por una configuración regional.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a>  ctype::char_type

Tipo que describe un carácter usado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *CharType*.

### <a name="example"></a>Ejemplo

Vea la función miembro [widen](#widen) para obtener un ejemplo que usa `char_type` como valor devuelto.

## <a name="ctype"></a>  ctype::ctype

Constructor de objetos de clase ctype que actúan como facetas de configuración regional para los caracteres.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs* valor entero utilizado para especificar el tipo de administración de memoria para el objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles de la *_Refs* parámetro y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: no se definen estos valores.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base `locale::facet` con **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="do_is"></a>  ctype::do_is

Función virtual a la que se llama para comprobar si un carácter individual tiene un atributo determinado, o para clasificar los atributos de cada carácter de un intervalo y almacenarlos en una matriz.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;


virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara que es el carácter que va a probarse.

*CH* los caracteres cuyos atributos se van a probar.

*primera* un puntero al primer carácter del intervalo cuyos atributos se van a clasificar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo cuyos atributos se van a clasificar.

*dest* un puntero al principio de la matriz donde se almacenarán los valores de máscara que caracterizan a los atributos de cada uno de los caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve un valor booleano que es **True** si el carácter probado tiene el atributo descrito por el valor de máscara; **False** si no puede tener el atributo.

La segunda función miembro devuelve una matriz que contiene los valores de máscara que caracterizan a los atributos de cada uno de los caracteres del intervalo.

### <a name="remarks"></a>Comentarios

La clase [ctype_base](../standard-library/ctype-base-class.md), de la que deriva ctype, proporciona los valores de máscara que clasifican los atributos de los caracteres. La primera función miembro puede aceptar expresiones para su primer parámetro que se conoce como máscaras de bits y está formado a partir de la combinación de valores de máscara por los operadores lógicos bit a bit (&#124; , & , ^ , ~).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [is](#is), que llama a `do_is`.

## <a name="do_narrow"></a>  ctype::do_narrow

Una función virtual llamada para convertir un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo **char** en el carácter nativo establecido.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;


virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter de tipo `Chartype` usa la configuración regional que para se va a convertir.

*valor predeterminado* el valor predeterminado que se asignará a la función miembro a caracteres de tipo `CharType` que no tienen caracteres equivalente de tipo **char**.

*primera* un puntero al primer carácter del intervalo de caracteres que se va a convertir.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se va a convertir.

*dest* un puntero al primer carácter de tipo const **char** del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve el carácter nativo de tipo char que corresponde con el carácter de parámetro de tipo `CharType` o *predeterminada* si no se ha definido ningún homólogo.

La segunda función miembro protegida devuelve un puntero al intervalo de destino de caracteres nativos convertidos a partir de caracteres de tipo `CharType`.

### <a name="remarks"></a>Comentarios

La segunda función miembro protegida plantilla almacena en `dest`[ `I`] el valor `do_narrow`( `first` [ `I`], `default`), para `I` en el intervalo [0, `last`  -  `first`).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [narrow](#narrow), que llama a `do_narrow`.

## <a name="do_scan_is"></a>  ctype::do_scan_is

Función virtual a la que se llama para buscar el primer carácter de un intervalo que coincide con una máscara especificada.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara que debe coincidir con un carácter.

*primera* un puntero al primer carácter del intervalo que se va a analizar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo que se va a analizar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que coincide con una máscara especificada. Si no existe este valor, la función devuelve *última*.

### <a name="remarks"></a>Comentarios

La función miembro protegida devuelve el puntero más pequeño `ptr` en el intervalo [ `first`, `last`) para el que [do_is](#do_is)( `maskVal`, * `ptr`) es True.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [scan_is](#scan_is), que llama a `do_scan_is`.

## <a name="do_scan_not"></a>  ctype::do_scan_not

Función virtual a la que se llama para buscar el primer carácter de un intervalo que no coincide con una máscara especificada.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara no se debe coincidir con un carácter.

*primera* un puntero al primer carácter del intervalo que se va a analizar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo que se va a analizar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que no coincide con una máscara especificada. Si no existe este valor, la función devuelve *última*.

### <a name="remarks"></a>Comentarios

La función miembro protegida devuelve el puntero más pequeño `ptr` en el intervalo [ `first`, `last`) para el que [do_is](#do_is)( `maskVal`, * `ptr`) es False.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [scan_not](#scan_not), que llama a `do_scan_not`.

## <a name="do_tolower"></a>  ctype::do_tolower

Función virtual a la que se llama para convertir a minúsculas un carácter o un intervalo de caracteres.

```cpp
virtual CharType do_tolower(CharType ch) const;


virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter que se va a convertir a minúsculas.

*primera* un puntero al primer carácter del intervalo de caracteres cuyos casos que se va a convertirse.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres cuyos casos que se va a convertirse.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve la forma en minúsculas del parámetro *ch*. Si no hay ninguna forma en minúsculas, devuelve *ch*. La segunda función miembro protegida devuelve *última*.

### <a name="remarks"></a>Comentarios

La segunda función de plantilla miembro protegida reemplaza cada elemento `first` [ `I`], para `I` en el intervalo [0, `last`  -  `first`), con `do_tolower`( `first` [ `I`]).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [tolower](#tolower), que llama a `do_tolower`.

## <a name="do_toupper"></a>  ctype::do_toupper

Función virtual a la que se llama para convertir a mayúsculas un carácter o un intervalo de caracteres.

```cpp
virtual CharType do_toupper(CharType ch) const;


virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter que se va a convertir a mayúsculas.

*primera* un puntero al primer carácter del intervalo de caracteres cuyos casos que se va a convertirse.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres cuyos casos que se va a convertirse.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve la forma en mayúsculas del parámetro *ch*. Si no hay ninguna forma en mayúsculas, devuelve *ch*. La segunda función miembro protegida devuelve *última*.

### <a name="remarks"></a>Comentarios

La segunda función de plantilla miembro protegida reemplaza cada elemento `first` [ `I`], para `I` en el intervalo [0, `last`  -  `first`), con `do_toupper`( `first` [ `I`]).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [toupper](#toupper), que llama a `do_toupper`.

## <a name="do_widen"></a>  ctype::do_widen

Una función virtual llamada para convierte un carácter de tipo **char** en el juego en el carácter correspondiente de tipo de caracteres nativo `CharType` usado por una configuración regional.

```cpp
virtual CharType do_widen(char byte) const;


virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parámetros

*bytes* el carácter de tipo **char** en el juego se conviertan de caracteres nativo.

*primera* un puntero al primer carácter del intervalo de caracteres que se va a convertir.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se va a convertir.

*dest* un puntero al primer carácter de tipo `CharType` del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve el carácter de tipo `CharType` que se corresponde con el carácter de parámetro de tipo nativo **char**.

La segunda función miembro protegida devuelve un puntero al intervalo de destino de caracteres de tipo `CharType` utilizado por una configuración regional convertida a partir de caracteres nativos de tipo **char**.

### <a name="remarks"></a>Comentarios

La segunda función de plantilla miembro protegida almacena en `dest`[ `I`] el valor `do_widen`( `first`[ `I`]), para `I` en el intervalo [0, `last` - `first`).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [widen](#widen), que llama a `do_widen`.

## <a name="is"></a>  ctype::is

Comprueba si un carácter individual tiene un atributo determinado, o clasifica los atributos de cada carácter de un intervalo y los almacena en una matriz.

```cpp
bool is(mask maskVal, CharType ch) const;


const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara que es el carácter que va a probarse.

*CH* los caracteres cuyos atributos se van a probar.

*primera* un puntero al primer carácter del intervalo cuyos atributos se van a clasificar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo cuyos atributos se van a clasificar.

*dest* un puntero al principio de la matriz donde se almacenarán los valores de máscara que caracterizan a los atributos de cada uno de los caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve **true** si el carácter probado tiene el atributo descrito por el valor de máscara; **false** si no puede tener el atributo.

La segunda función miembro devuelve un puntero al último carácter del intervalo cuyos atributos se van a clasificar.

### <a name="remarks"></a>Comentarios

La clase [ctype_base (Clase)](../standard-library/ctype-base-class.md), de la que deriva ctype, proporciona los valores de máscara que clasifican los atributos de los caracteres. La primera función miembro puede aceptar expresiones para su primer parámetro que se conoce como máscaras de bits y está formado a partir de la combinación de valores de máscara por los operadores lógicos bit a bit (&#124; , & , ^ , ~).

### <a name="example"></a>Ejemplo

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a>  ctype::narrow

Convierte los caracteres de tipo `CharType` utilizado por una configuración regional para los caracteres correspondientes de tipo **char** en el carácter nativo establecido.

```cpp
char narrow(CharType ch, char default = '\0') const;


const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter de tipo `Chartype` usa la configuración regional que para se va a convertir.

*valor predeterminado* el valor predeterminado que se asignará a la función miembro a caracteres de tipo `CharType` que no tienen caracteres equivalente de tipo **char**.

*primera* un puntero al primer carácter del intervalo de caracteres que se va a convertir.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se va a convertir.

*dest* un puntero al primer carácter de tipo const **char** del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve el carácter de tipo nativo **char** que se corresponde con el carácter de parámetro de tipo `CharType default` si homólogo no está definido.

La segunda función miembro devuelve un puntero al intervalo de destino de caracteres nativos convertidos a partir de caracteres de tipo `CharType`.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [do_narrow](#do_narrow)(`ch`, `default`). La segunda función miembro devuelve [do_narrow](#do_narrow) (`first`, `last`, `default`, `dest`). Solo se garantiza que los caracteres de código fuente básicos tengan una imagen inversa única `CharType` en `narrow`. Para estos caracteres de código fuente básicos, la siguiente invariable contiene: `narrow` ( [widen](#widen) ( **c** ), 0 ) == **c**.

### <a name="example"></a>Ejemplo

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a>  ctype::scan_is

Busca el primer carácter de un intervalo que coincide con una máscara especificada.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara que debe coincidir con un carácter.

*primera* un puntero al primer carácter del intervalo que se va a analizar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo que se va a analizar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que coincide con una máscara especificada. Si no existe este valor, la función devuelve *última*.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_scan_is](#do_scan_is)(`maskVal`, `first`, `last`).

### <a name="example"></a>Ejemplo

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a>  ctype::scan_not

Busca el primer carácter de un intervalo que no coincide con una máscara especificada.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal* el valor de máscara no se debe coincidir con un carácter.

*primera* un puntero al primer carácter del intervalo que se va a analizar.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo que se va a analizar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que no coincide con una máscara especificada. Si no existe este valor, la función devuelve *última*.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_scan_not](#do_scan_not)(`maskVal`, `first`, `last`).

### <a name="example"></a>Ejemplo

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a>  ctype::tolower

Convierte a minúsculas un carácter o un intervalo de caracteres.

```cpp
CharType tolower(CharType ch) const;


const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter que se va a convertir a minúsculas.

*primera* un puntero al primer carácter del intervalo de caracteres cuyos casos que se va a convertirse.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres cuyos casos que se va a convertirse.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la forma en minúsculas del parámetro *ch*. Si no hay ninguna forma en minúsculas, devuelve *ch*.

La segunda función miembro devuelve *última*.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [do_tolower](#do_tolower)(`ch`). La segunda función miembro devuelve [do_tolower](#do_tolower)(`first`, `last`).

### <a name="example"></a>Ejemplo

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a>  ctype::toupper

Convierte a mayúsculas un carácter o un intervalo de caracteres.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*CH* el carácter que se va a convertir a mayúsculas.

*primera* un puntero al primer carácter del intervalo de caracteres cuyos casos que se va a convertirse.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres cuyos casos que se va a convertirse.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la forma en mayúsculas del parámetro *ch*. Si no hay ninguna forma en mayúsculas, devuelve *ch*.

La segunda función miembro devuelve *última*.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [do_toupper](#do_toupper)(`ch`). La segunda función miembro devuelve [do_toupper](#do_toupper)( `first`, `last`).

### <a name="example"></a>Ejemplo

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a>  ctype::widen

Convierte un carácter de tipo **char** en el juego en el carácter correspondiente de tipo de caracteres nativo `CharType` usado por una configuración regional.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parámetros

*bytes* establece el carácter de tipo char en el carácter nativo que para se va a convertir.

*primera* un puntero al primer carácter del intervalo de caracteres que se va a convertir.

*último* un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se va a convertir.

*dest* un puntero al primer carácter de tipo `CharType` del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve el carácter de tipo `CharType` que se corresponde con el carácter de parámetro de tipo nativo **char**.

La segunda función miembro devuelve un puntero al intervalo de destino de caracteres de tipo `CharType` utilizado por una configuración regional convertida a partir de caracteres nativos de tipo **char**.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [do_widen](#do_widen)(`byte`). La segunda función miembro devuelve [do_widen](#do_widen)(`first`, `last`, `dest`).

### <a name="example"></a>Ejemplo

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
