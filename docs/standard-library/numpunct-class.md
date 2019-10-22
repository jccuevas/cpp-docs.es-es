---
title: numpunct (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: 07285f5c014db1ddf419c372913cac0364538a55
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689221"
---
# <a name="numpunct-class"></a>numpunct (Clase)

Una plantilla de clase que describe un objeto que puede actuar como una faceta local para describir las secuencias de tipo `CharType` usar para representar información sobre el formato y la puntuación de expresiones numéricas y booleanas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *CharType*
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[numpunct](#numpunct)|Constructor para los objetos de tipo `numpunct`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[string_type](#string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[decimal_point](#decimal_point)|Devuelve un elemento específico de la configuración regional que se va a usar como separador decimal.|
|[do_decimal_point](#do_decimal_point)|Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador decimal.|
|[do_falsename](#do_falsename)|Función miembro virtual protegida a la que se llama para devolver una cadena que se va a usar como representación de texto del valor **false**.|
|[do_grouping](#do_grouping)|Función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional con el fin de determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.|
|[do_thousands_sep](#do_thousands_sep)|Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador de miles.|
|[do_truename](#do_truename)|Una función miembro virtual protegida a la que se llama para devolver una cadena que se va a usar como una representación de texto del valor **true**.|
|[falsename](#falsename)|Devuelve una cadena que se va a usar como una representación de texto del valor **false**.|
|[grouping](#grouping)|Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.|
|[thousands_sep](#thousands_sep)|Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.|
|[truename](#truename)|Devuelve una cadena que se va a usar como representación de texto del valor **true**.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> numpunct::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="decimal_point"></a> numpunct::decimal_point

Devuelve un elemento específico de la configuración regional que se va a usar como separador decimal.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Valor devuelto

Un elemento específico de la configuración regional que se va a usar como separador decimal.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Ejemplo

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="do_decimal_point"></a> numpunct::do_decimal_point

Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador decimal.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Valor devuelto

Un elemento específico de la configuración regional que se va a usar como separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [decimal_point](#decimal_point), donde `decimal_point` llama a la función miembro virtual.

## <a name="do_falsename"></a> numpunct::do_falsename

La función miembro virtual protegida devuelve una secuencia que se va a usar como una representación de texto del valor **false**.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene una secuencia que se va a usar como una representación de texto del valor **false**.

### <a name="remarks"></a>Comentarios

La función miembro devuelve la cadena "false" para representar el valor **false** en todas las configuraciones regionales.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [falsename](#falsename), donde `falsename` llama a la función miembro virtual.

## <a name="do_grouping"></a> numpunct::do_grouping

Función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional con el fin de determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Valor devuelto

Una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal. La codificación es la misma que para **lconv::grouping**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [agrupación](#grouping), donde `grouping` llama a la función miembro virtual.

## <a name="do_thousands_sep"></a> numpunct::do_thousands_sep

Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador de miles.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida devuelve un elemento específico de la configuración regional de tipo `CharType` que se va a usar como separador de grupo a la izquierda de cualquier separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [thousands_sep](#thousands_sep), donde `thousands_sep` llama a la función miembro virtual.

## <a name="do_truename"></a> numpunct::do_truename

Una función miembro virtual protegida a la que se llama para devolver una cadena que se va a usar como una representación de texto del valor **true**.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Comentarios

Una cadena que se va a usar como una representación de texto del valor **true**.

Todas las configuraciones regionales devuelven una cadena "true" para representar el valor **true**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [truename](#truename), donde `truename` llama a la función miembro virtual.

## <a name="falsename"></a> numpunct::falsename

Devuelve una cadena que se va a usar como una representación de texto del valor **false**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene una secuencia de `CharType`s que se va a usar como representación de texto del valor **false**.

### <a name="remarks"></a>Comentarios

La función miembro devuelve la cadena "false" para representar el valor **false** en todas las configuraciones regionales.

La función miembro devuelve [do_falsename](#do_falsename).

### <a name="example"></a>Ejemplo

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="grouping"></a> numpunct::grouping

Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Valor devuelto

Una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_grouping](#do_grouping).

### <a name="example"></a>Ejemplo

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
```

## <a name="numpunct"></a> numpunct::numpunct

Constructor para los objetos de tipo `numpunct`.

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Refs*
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="string_type"></a> numpunct::string_type

Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de la plantilla de clase [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de puntuación.

## <a name="thousands_sep"></a> numpunct::thousands_sep

Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Valor devuelto

Un elemento específico de la configuración regional que se va a usar como separador de miles.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Ejemplo

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="truename"></a> numpunct::truename

Devuelve una cadena que se va a usar como representación de texto del valor **true**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Valor devuelto

Una cadena que se va a usar como una representación de texto del valor **true**.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_truename](#do_truename).

Todas las configuraciones regionales devuelven una cadena "true" para representar el valor **true**.

### <a name="example"></a>Ejemplo

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)\
[facet (Clase)](../standard-library/locale-class.md#facet_class)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
