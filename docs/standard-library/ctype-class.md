---
title: ctype (Clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: dae6f62a0eda9263986a77b82754596d17be94e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373163"
---
# <a name="ctype-class"></a>ctype (Clase)

Clase que proporciona una faceta que se emplea para clasificar los caracteres, pasar de mayúsculas a minúsculas y convertir entre el juego de caracteres nativo y el que usa la configuración regional.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar caracteres.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`. Se proporciona a los criterios de clasificación un tipo de máscara de bits anidado en el ctype_base de la clase base.

La biblioteca estándar C++ define dos especializaciones explícitas de esta plantilla de clase:

- `ctype<char>`, una especialización explícita cuyas diferencias se describen por separado. Para obtener más información, vea [ctype&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, que trata los elementos como caracteres anchos.

Otras especializaciones de `ctype<CharType>`la plantilla de clase:

- Convierta un valor *ch* de tipo *CharType* en `(char)ch`un valor de tipo **char** con la expresión .

- Convierta un *byte* de valor de tipo **char** en un valor de tipo *CharType* con la expresión `CharType(byte)`.

Todas las demás **char** operaciones se realizan en valores `ctype<char>`char de la misma manera que para la especialización explícita.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ctype](#ctype)|Constructor de objetos de clase `ctype` que actúan como facetas de configuración regional para los caracteres.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que describe un carácter usado por una configuración regional.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[do_is](#do_is)|Función virtual a la que se llama para comprobar si un carácter individual tiene un atributo determinado, o para clasificar los atributos de cada carácter de un intervalo y almacenarlos en una matriz.|
|[do_narrow](#do_narrow)|Una función virtual llamada para `CharType` convertir un carácter de tipo utilizado por una configuración regional al carácter correspondiente de tipo **char** en el juego de caracteres nativo.|
|[do_scan_is](#do_scan_is)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que coincide con una máscara especificada.|
|[do_scan_not](#do_scan_not)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que no coincide con una máscara especificada.|
|[do_tolower](#do_tolower)|Función virtual a la que se llama para convertir a minúsculas un carácter o un intervalo de caracteres.|
|[do_toupper](#do_toupper)|Función virtual a la que se llama para convertir a mayúsculas un carácter o un intervalo de caracteres.|
|[do_widen](#do_widen)|Una función virtual llamada para **char** convertir un carácter de tipo char `CharType` en el juego de caracteres nativo al carácter correspondiente de tipo utilizado por una configuración regional.|
|[is](#is)|Comprueba si un carácter individual tiene un atributo determinado, o clasifica los atributos de cada carácter de un intervalo y los almacena en una matriz.|
|[narrow](#narrow)|Convierte un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo char del juego de caracteres nativo.|
|[scan_is](#scan_is)|Busca el primer carácter de un intervalo que coincide con una máscara especificada.|
|[scan_not](#scan_not)|Busca el primer carácter de un intervalo que no coincide con una máscara especificada.|
|[tolower](#tolower)|Convierte a minúsculas un carácter o un intervalo de caracteres.|
|[toupper](#toupper)|Convierte a mayúsculas un carácter o un intervalo de caracteres.|
|[widen](#widen)|Convierte un carácter de tipo **char** en el juego `CharType` de caracteres nativo en el carácter correspondiente de tipo utilizado por una configuración regional.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="ctypechar_type"></a><a name="char_type"></a>ctype::char_type

Tipo que describe un carácter usado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *CharType*.

### <a name="example"></a>Ejemplo

Vea la función miembro [widen](#widen) para obtener un ejemplo que usa `char_type` como valor devuelto.

## <a name="ctypectype"></a><a name="ctype"></a>ctype::ctype

Constructor de objetos de clase ctype que actúan como facetas de configuración regional para los caracteres.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: Estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa `locale::facet` su objeto base con `_Refs` **locale::**[faceta](../standard-library/locale-class.md#facet_class)( ).

## <a name="ctypedo_is"></a><a name="do_is"></a>ctype::do_is

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

*maskVal*\
El valor de máscara para el que se probará el carácter.

*Ch*\
Los caracteres cuyos atributos se van a probar.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres cuyos atributos se van a clasificar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo cuyos atributos se van a clasificar.

*Dest*\
Un puntero al principio de la matriz en que se van a almacenar los valores de máscara que caracterizan a los atributos de cada uno de los caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve un valor booleano que es **True** si el carácter probado tiene el atributo descrito por el valor de máscara; **False** si no puede tener el atributo.

La segunda función miembro devuelve una matriz que contiene los valores de máscara que caracterizan a los atributos de cada uno de los caracteres del intervalo.

### <a name="remarks"></a>Observaciones

La clase [ctype_base](../standard-library/ctype-base-class.md), de la que deriva ctype, proporciona los valores de máscara que clasifican los atributos de los caracteres. La primera función miembro puede aceptar expresiones para su primer parámetro que se conoce como máscaras de bits y está formado a partir de la combinación de valores de máscara por los operadores lógicos bit a bit (&#124; , & , ^ , ~).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [is](#is), que llama a `do_is`.

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a>ctype::do_narrow

Una función virtual llamada para `CharType` convertir un carácter de tipo utilizado por una configuración regional al carácter correspondiente de tipo **char** en el juego de caracteres nativo.

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

*Ch*\
El carácter de tipo `Chartype` usado por la configuración regional que se va a convertir.

*Predeterminado*\
El valor predeterminado que asignará la función `CharType` miembro a caracteres de tipo que no tienen caracteres homólogos de tipo **char**.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que se va convertir.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se van a convertir.

*Dest*\
Un puntero const al primer carácter de tipo **char** en el intervalo de destino que almacena el intervalo convertido de caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve el carácter nativo de `CharType` tipo char que corresponde al carácter de parámetro de tipo o *valor predeterminado* si no se define ningún homólogo.

La segunda función miembro protegida devuelve un puntero al intervalo de destino de caracteres nativos convertidos a partir de caracteres de tipo `CharType`.

### <a name="remarks"></a>Observaciones

La segunda función de `dest` `I`plantilla miembro `do_narrow` `first` protegida `I`almacena `default`en `I` [ ] el `last`  - valor ( [ ], ), en el intervalo [0, `first`).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [narrow](#narrow), que llama a `do_narrow`.

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a>ctype::do_scan_is

Función virtual a la que se llama para buscar el primer carácter de un intervalo que coincide con una máscara especificada.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal*\
El valor de máscara que debe coincidir con un carácter.

*Primero*\
Un puntero al primer carácter del intervalo que se va a examinar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo que se va a examinar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que coincide con una máscara especificada. Si no existe tal valor, la función devuelve *last*.

### <a name="remarks"></a>Observaciones

La función miembro protegida `ptr` devuelve el `first` `last`puntero más pequeño en el intervalo [ , ) para el que [do_is](#do_is)( `maskVal`, \* `ptr`) es true.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [scan_is](#scan_is), que llama a `do_scan_is`.

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a>ctype::do_scan_not

Función virtual a la que se llama para buscar el primer carácter de un intervalo que no coincide con una máscara especificada.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal*\
El valor de máscara que no debe coincidir con un carácter.

*Primero*\
Un puntero al primer carácter del intervalo que se va a examinar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo que se va a examinar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que no coincide con una máscara especificada. Si no existe tal valor, la función devuelve *last*.

### <a name="remarks"></a>Observaciones

La función miembro protegida `ptr` devuelve el `first` `last`puntero más pequeño del intervalo [ , ) para el que [do_is](#do_is)( `maskVal`, \* `ptr`) es false.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [scan_not](#scan_not), que llama a `do_scan_not`.

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a>ctype::do_tolower

Función virtual a la que se llama para convertir a minúsculas un carácter o un intervalo de caracteres.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El carácter que se va a convertir en minúscula.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve la forma en minúsculas del parámetro *ch*. Si no existe ninguna forma en minúsculas, devuelve *ch*. La segunda función miembro protegida devuelve *last*.

### <a name="remarks"></a>Observaciones

La segunda función de plantilla `first` `I`miembro protegida `I` reemplaza cada elemento `last`  -  `first`[ `do_tolower` `first` ], ya que en el intervalo [0, ), por ( [ `I`]).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [tolower](#tolower), que llama a `do_tolower`.

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a>ctype::do_toupper

Función virtual a la que se llama para convertir a mayúsculas un carácter o un intervalo de caracteres.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El carácter que se va a convertir en mayúscula.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida devuelve la forma en mayúsculas del parámetro *ch*. Si no existe ninguna forma en mayúsculas, devuelve *ch*. La segunda función miembro protegida devuelve *last*.

### <a name="remarks"></a>Observaciones

La segunda función de plantilla `first` `I`miembro protegida `I` reemplaza cada elemento `last`  -  `first`[ `do_toupper` `first` ], ya que en el intervalo [0, ), por ( [ `I`]).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [toupper](#toupper), que llama a `do_toupper`.

## <a name="ctypedo_widen"></a><a name="do_widen"></a>ctype::do_widen

Una función virtual llamada para **char** convertir un carácter de tipo char `CharType` en el juego de caracteres nativo al carácter correspondiente de tipo utilizado por una configuración regional.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parámetros

*Byte*\
Carácter de tipo **char** en el juego de caracteres nativo que se va a convertir.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que se va convertir.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se van a convertir.

*Dest*\
Un puntero al primer carácter de tipo `CharType` del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro protegida `CharType` devuelve el carácter de tipo que corresponde al carácter de parámetro de tipo nativo **char**.

La segunda función miembro protegida devuelve un puntero `CharType` al intervalo de destino de caracteres de tipo utilizado por una configuración regional convertida a partir de caracteres nativos de tipo **char**.

### <a name="remarks"></a>Observaciones

La segunda función de plantilla miembro protegida almacena en `dest`[ `I`] el valor `do_widen`( `first`[ `I`]), para `I` en el intervalo [0, `last` - `first`).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [widen](#widen), que llama a `do_widen`.

## <a name="ctypeis"></a><a name="is"></a>ctype::is

Comprueba si un carácter individual tiene un atributo determinado, o clasifica los atributos de cada carácter de un intervalo y los almacena en una matriz.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parámetros

*maskVal*\
El valor de máscara para el que se probará el carácter.

*Ch*\
Los caracteres cuyos atributos se van a probar.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres cuyos atributos se van a clasificar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo cuyos atributos se van a clasificar.

*Dest*\
Un puntero al principio de la matriz en que se van a almacenar los valores de máscara que caracterizan a los atributos de cada uno de los caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve **true** si el carácter probado tiene el atributo descrito por el valor de máscara; **false** si no tiene el atributo.

La segunda función miembro devuelve un puntero al último carácter del intervalo cuyos atributos se van a clasificar.

### <a name="remarks"></a>Observaciones

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

## <a name="ctypenarrow"></a><a name="narrow"></a>ctype::narrow

Convierte caracteres `CharType` de tipo utilizados por una configuración regional en los caracteres correspondientes de tipo **char** en el juego de caracteres nativo.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El carácter de tipo `Chartype` usado por la configuración regional que se va a convertir.

*Predeterminado*\
El valor predeterminado que asignará la función `CharType` miembro a caracteres de tipo que no tienen caracteres homólogos de tipo **char**.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que se va convertir.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se van a convertir.

*Dest*\
Un puntero const al primer carácter de tipo **char** en el intervalo de destino que almacena el intervalo convertido de caracteres.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve **char** el carácter nativo de `CharType default` tipo char que corresponde al carácter de parámetro de tipo si no se define su homólogo.

La segunda función miembro devuelve un puntero al intervalo de destino de caracteres nativos convertidos a partir de caracteres de tipo `CharType`.

### <a name="remarks"></a>Observaciones

La primera función`ch`miembro `default`devuelve [do_narrow](#do_narrow)( , ). La segunda función`first`miembro `last` `default`devuelve `dest` [do_narrow](#do_narrow) ( , , , ). Solo se garantiza que los caracteres de código fuente básicos tengan una imagen inversa única `CharType` en `narrow`. Para estos caracteres de código fuente básicos, la siguiente invariable contiene: `narrow` ( [widen](#widen) ( **c** ), 0 ) == **c**.

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

## <a name="ctypescan_is"></a><a name="scan_is"></a>ctype::scan_is

Busca el primer carácter de un intervalo que coincide con una máscara especificada.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal*\
El valor de máscara que debe coincidir con un carácter.

*Primero*\
Un puntero al primer carácter del intervalo que se va a examinar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo que se va a examinar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que coincide con una máscara especificada. Si no existe tal valor, la función devuelve *last*.

### <a name="remarks"></a>Observaciones

La función miembro`maskVal` `first`devuelve `last` [do_scan_is](#do_scan_is)( , , ).

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

## <a name="ctypescan_not"></a><a name="scan_not"></a>ctype::scan_not

Busca el primer carácter de un intervalo que no coincide con una máscara especificada.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*maskVal*\
El valor de máscara que no debe coincidir con un carácter.

*Primero*\
Un puntero al primer carácter del intervalo que se va a examinar.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo que se va a examinar.

### <a name="return-value"></a>Valor devuelto

Un puntero al primer carácter de un intervalo que no coincide con una máscara especificada. Si no existe tal valor, la función devuelve *last*.

### <a name="remarks"></a>Observaciones

La función miembro`maskVal` `first`devuelve `last` [do_scan_not](#do_scan_not)( , , ).

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

## <a name="ctypetolower"></a><a name="tolower"></a>ctype::tolower

Convierte a minúsculas un carácter o un intervalo de caracteres.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El carácter que se va a convertir en minúscula.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la forma en minúsculas del parámetro *ch*. Si no existe ninguna forma en minúsculas, devuelve *ch*.

La segunda función miembro devuelve *last*.

### <a name="remarks"></a>Observaciones

La primera función`ch`miembro devuelve [do_tolower](#do_tolower)( ). La segunda función`first`miembro `last`devuelve [do_tolower](#do_tolower)( , ).

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

## <a name="ctypetoupper"></a><a name="toupper"></a>ctype::toupper

Convierte a mayúsculas un carácter o un intervalo de caracteres.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El carácter que se va a convertir en mayúscula.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que va a pasar de mayúsculas a minúsculas (o viceversa).

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la forma en mayúsculas del parámetro *ch*. Si no existe ninguna forma en mayúsculas, devuelve *ch*.

La segunda función miembro devuelve *last*.

### <a name="remarks"></a>Observaciones

La primera función`ch`miembro devuelve [do_toupper](#do_toupper)( ). La segunda función `first`miembro `last`devuelve [do_toupper](#do_toupper)( , ).

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

## <a name="ctypewiden"></a><a name="widen"></a>ctype::widen

Convierte un carácter de tipo **char** en el juego `CharType` de caracteres nativo en el carácter correspondiente de tipo utilizado por una configuración regional.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parámetros

*Byte*\
El carácter de tipo char en el juego de caracteres nativo que se convertirá.

*Primero*\
Un puntero al primer carácter del intervalo de caracteres que se va convertir.

*Última*\
Un puntero al carácter inmediatamente después del último carácter del intervalo de caracteres que se van a convertir.

*Dest*\
Un puntero al primer carácter de tipo `CharType` del intervalo de destino que almacena el intervalo de caracteres convertido.

### <a name="return-value"></a>Valor devuelto

La primera función miembro `CharType` devuelve el carácter de tipo que corresponde al carácter de parámetro de tipo nativo **char**.

La segunda función miembro devuelve un puntero `CharType` al intervalo de destino de caracteres de tipo utilizado por una configuración regional convertida a partir de caracteres nativos de tipo **char**.

### <a name="remarks"></a>Observaciones

La primera función`byte`miembro devuelve [do_widen](#do_widen)( ). La segunda función`first`miembro `last` `dest`devuelve [do_widen](#do_widen)( , , ).

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

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
