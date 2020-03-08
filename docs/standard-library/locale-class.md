---
title: locale (Clase)
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 551bca93a30bee52dc4c838864df28cb747d91df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856558"
---
# <a name="locale-class"></a>locale (Clase)

La clase que describe un objeto de configuración regional que encapsula la información específica de la configuración regional como un conjunto de facetas que definen colectivamente un entorno traducido y adaptado concreto.

## <a name="syntax"></a>Sintaxis

```cpp
class locale;
```

## <a name="remarks"></a>Observaciones

Una faceta es un puntero a un objeto de una clase derivada de la clase [facet](#facet_class) que tiene un objeto público con el formato:

```cpp
static locale::id id;
```

Puede definir un conjunto abierto de estas facetas. También puede crear un objeto de configuración regional que designe un número arbitrario de facetas.

Los grupos predefinidos de estas facetas representan las [categorías de configuración regional](#category) administradas tradicionalmente en la biblioteca estándar de C por la función `setlocale`.

La categoría `collate` (LC_COLLATE) incluye las caras:

```cpp
collate<char>
collate<wchar_t>
```

La categoría `ctype` (LC_CTYPE) incluye las caras:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

La categoría `monetary` (LC_MONETARY) incluye las caras:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

La categoría `numeric` (LC_NUMERIC) incluye las caras:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

La categoría `time` (LC_TIME) incluye las caras:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

La categoría `messages` (LC_MESSAGES) incluye las caras:

```cpp
messages<char>
messages<wchar_t>
```

(La última categoría es necesaria para POSIX, pero no para el estándar de C).

Las clases `iostream` utilizan algunas de estas caras predefinidas para controlar la conversión de valores numéricos a y desde secuencias de texto.

Un objeto de clase locale clase también almacena un nombre de configuración regional como un objeto de la clase [string](../standard-library/string-typedefs.md#string). El uso de un nombre no válido de configuración regional para construir una faceta o un objeto de configuración regional produce un objeto de la clase [runtime_error](../standard-library/runtime-error-class.md). El nombre de la configuración regional almacenada es `"*"` si el objeto de configuración regional no puede estar seguro de que una configuración regional de estilo C corresponde exactamente a la representada por el objeto. De lo contrario, puede establecer una configuración regional coincidente dentro de la biblioteca estándar de C, para algunos `locale_object`del objeto de configuración regional, llamando a `setlocale(LC_ALL , locale_object.`[nombre](#name)`().c_str())`.

En esta implementación, también puede llamar a la función miembro estática:

```cpp
static locale empty();
```

para construir un objeto de configuración regional que no tiene ninguna faceta. También es una configuración regional transparente. Si las funciones de plantilla [has_facet](../standard-library/locale-functions.md#has_facet) y [use_facet](../standard-library/locale-functions.md#use_facet) no encuentran la faceta solicitada en una configuración regional transparente, consultan primero la configuración regional global y después, si es transparente, la configuración regional clásica. Por lo tanto, puede escribir:

```cpp
cout.imbue(locale::empty());
```

Las inserciones posteriores a [`cout`](../standard-library/iostream.md#cout) se corrigen según el estado actual de la configuración regional global. Incluso puede escribir:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Las reglas de formato numérico para las inserciones posteriores a `cout` son las mismas que en la configuración regional de C, incluso aunque la configuración regional global proporcione reglas que cambian para insertar fechas y cantidades monetarias.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[locale](#locale)|Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[category](#category)|Tipo entero que proporciona valores de máscara de bits para denotar familias de facetas estándar.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[combine](#combine)|Inserta una faceta de una configuración regional especificada en una configuración regional de destino.|
|[name](#name)|Devuelve el nombre de configuración regional almacenado.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[clásico](#classic)|La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.|
|[global](#global)|Restablece la configuración regional predeterminada del programa.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna una configuración regional.|
|[operator!=](#op_neq)|Comprueba si dos configuraciones regionales son distintas.|
|[operator( )](#op_call)|Compara dos objetos `basic_string`.|
|[operator==](#op_eq_eq)|Comprueba si dos configuraciones regionales son iguales.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[facet](#facet_class)|Clase que actúa como clase base para todas las facetas de configuración regional.|
|[`id`](#id_class)|La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<configuración regional >

**Espacio de nombres:** std

## <a name="category"></a>  locale::category

Tipo entero que proporciona valores de máscara de bits para denotar familias de facetas estándar.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de un tipo **int** que puede representar un grupo de elementos distintos de un tipo de máscara de máscara local a la configuración regional de clase o se puede usar para representar cualquiera de las categorías de configuración regional de C correspondientes. Los elementos son:

- `collate`, correspondiente a la categoría C LC_COLLATE

- `ctype`, correspondiente a la categoría C LC_CTYPE

- `monetary`, correspondiente a la categoría C LC_MONETARY

- `numeric`, correspondiente a la categoría C LC_NUMERIC

- `time`, correspondiente a la categoría C LC_TIME

- `messages`, correspondiente a la categoría POSIX LC_MESSAGES

Dos valores más útiles son:

- `none`, correspondiente a ninguna de las categorías de C

- `all`, correspondiente a la Unión de C de todas las categorías LC_ALL

Puede representar un grupo arbitrario de categorías utilizando `OR` con estas constantes, como en `monetary` &#124; `time`.

## <a name="classic"></a>  locale::classic

La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Valor devuelto

Referencia a la configuración regional de C.

### <a name="remarks"></a>Observaciones

La configuración regional de C clásica es la configuración regional ASCII en Inglés de EE. UU. en la biblioteca estándar de C. Es la configuración regional que se usa implícitamente en programas que no están internacionalizados.

### <a name="example"></a>Ejemplo

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="combine"></a>  locale::combine

Inserta una faceta de una configuración regional especificada en una configuración regional de destino.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parámetros

*source_locale*\
Configuración regional que contiene la faceta que se va a insertar en la configuración regional de destino.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve un objeto de configuración regional que reemplaza a o agrega a **\*esta** `Facet` de faceta aparece en *source_locale*.

### <a name="example"></a>Ejemplo

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet_class"></a>  Clase facet

Clase que actúa como clase base para todas las facetas de configuración regional.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Observaciones

No se puede copiar o asignar un objeto de clase `facet`. Puede crear y destruir objetos derivados de la clase `locale::facet`, pero no los objetos de la clase base correcta. Normalmente, se crea un objeto `_Myfac` derivado de `facet` al construir un `locale`, como en `locale loc(locale::classic(), new _Myfac);`

En tales casos, el constructor de la clase base `facet` debe tener un argumento de *referencias* cero. Cuando el objeto ya no es necesario, se elimina, por lo que solo se proporciona un argumento de *referencias* distinto de cero en los casos excepcionales en los que se asume la responsabilidad de la duración del objeto.

## <a name="global"></a>  locale::global

Restablece la configuración regional predeterminada del programa. Esta llamada afecta a la configuración regional global de C y C++.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parámetros

*new_default_locale*\
Configuración regional que el programa usará como configuración regional predeterminada.

### <a name="return-value"></a>Valor devuelto

Configuración regional anterior al restablecimiento de la configuración regional predeterminada.

### <a name="remarks"></a>Observaciones

Al inicio del programa, la configuración regional global es igual que la configuración regional clásica. La función `global()` llama a `setlocale( LC_ALL, loc.name. c_str())` para establecer una configuración regional coincidente en la biblioteca estándar de C++.

### <a name="example"></a>Ejemplo

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id_class"></a>  Clase id

La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Observaciones

La clase de miembro describe el objeto de miembro estático requerido por cada faceta de configuración regional única. No se puede copiar o asignar un objeto de clase `id`.

## <a name="locale"></a>  locale::locale

Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional. También incluye un destructor.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Parámetros

*locale_name*\
Nombre de una configuración regional.

*from_locale*\
Configuración regional que se va a copiar en la construcción de la nueva configuración regional.

*Otros*\
Configuración regional de la que se va a seleccionar una categoría.

*new_category*\
Categoría que se va a sustituir en la configuración regional construida.

*new_facet*\
Faceta que se va a sustituir en la configuración regional construida.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el objeto para que coincida con la configuración regional global. Los constructores segundo y tercero inicializan todas las categorías de configuración regional para tener un comportamiento coherente con el nombre de configuración regional *locale_name*. Los constructores restantes copian *from_locale*, con las excepciones indicadas:

`locale(const locale& from_locale, const locale& Other, category new_category);`

reemplaza de *otras* caras correspondientes a una categoría c para la que c & *new_category* es distinto de cero.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

reemplaza de `locale(locale_name, all)` esas caras correspondientes a una categoría *replace_category* para la que `replace_category & new_category` es distinto de cero.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

reemplaza en (o agrega a) *from_locale* la *new_facet*de faceta, si *new_facet* no es un puntero nulo.

Si el nombre de la configuración regional *locale_name* es un puntero nulo o no es válido, la función produce [runtime_error](../standard-library/runtime-error-class.md).

### <a name="example"></a>Ejemplo

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="name"></a>  locale::name

Devuelve el nombre de configuración regional almacenado.

```cpp
string name() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que proporciona el nombre de la configuración regional.

### <a name="example"></a>Ejemplo

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="op_eq"></a>configuración regional:: Operator =

Asigna una configuración regional.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="op_neq"></a>  locale::operator!=

Comprueba si dos configuraciones regionales son distintas.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Una de las configuraciones regionales cuya desigualdad se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Valor booleano que es **true** si las configuraciones regionales no son copias de la misma configuración regional. Es **false** si las configuraciones regionales son copias de la misma configuración regional.

### <a name="remarks"></a>Observaciones

Dos configuraciones regionales son iguales si son la misma configuración regional, si una es una copia de la otra, o si tienen nombres idénticos.

### <a name="example"></a>Ejemplo

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="op_call"></a>  locale::operator()

Compara dos objetos `basic_string`.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cadena izquierda.

\ *derecha*
Cadena derecha.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve:

- -1 si la primera secuencia compara menos que la segunda secuencia.

- +1 si la segunda secuencia compara menos que la primera secuencia.

- 0 si las secuencias son equivalentes.

### <a name="remarks"></a>Observaciones

La función miembro ejecuta eficazmente:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Significa que puede usar un objeto de configuración regional como un objeto de función.

### <a name="example"></a>Ejemplo

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="op_eq_eq"></a>  locale::operator==

Comprueba si dos configuraciones regionales son iguales.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Una de las configuraciones regionales cuya igualdad se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Valor booleano que es **true** si las configuraciones regionales son copias de la misma configuración regional. Es **false** si las configuraciones regionales no son copias de la misma configuración regional.

### <a name="remarks"></a>Observaciones

Dos configuraciones regionales son iguales si son la misma configuración regional, si una es una copia de la otra, o si tienen nombres idénticos.

### <a name="example"></a>Ejemplo

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Consulte también

[\<locale>](../standard-library/locale.md)\
[Páginas de códigos](../c-runtime-library/code-pages.md)\
[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
