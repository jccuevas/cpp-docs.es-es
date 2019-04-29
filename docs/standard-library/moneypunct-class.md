---
title: moneypunct (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 750b61100f7e3fe15851fffbedeb5b60d4d7034f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349126"
---
# <a name="moneypunct-class"></a>moneypunct (Clase)

La clase de plantilla describe un objeto que puede actuar como una faceta de configuración regional para describir las secuencias de tipo *CharType* utilizado para representar un campo de entrada monetario o un campo de salida monetario. Si el parámetro de plantilla *Intl* es *true*, se respetan las convenciones internacionales.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parámetros

*CharType*<br/>
Tipo usado dentro de un programa para codificar caracteres.

*Intl*<br/>
Una marca que especifica si las convenciones internacionales deben respetarse.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

El objeto estático constante intl almacena el valor del parámetro de plantilla *Intl*.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[moneypunct](#moneypunct)|Constructor de objetos de tipo `moneypunct`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[string_type](#string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[curr_symbol](#curr_symbol)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.|
|[decimal_point](#decimal_point)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como separador decimal.|
|[do_curr_symbol](#do_curr_symbol)|Una función miembro virtual protegida que devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.|
|[do_decimal_point](#do_decimal_point)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador decimal.|
|[do_frac_digits](#do_frac_digits)|La función miembro virtual protegida devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha de cualquier separador decimal.|
|[do_grouping](#do_grouping)|La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.|
|[do_neg_format](#do_neg_format)|Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.|
|[do_negative_sign](#do_negative_sign)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.|
|[do_pos_format](#do_pos_format)|Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.|
|[do_positive_sign](#do_positive_sign)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.|
|[do_thousands_sep](#do_thousands_sep)|Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador de miles.|
|[frac_digits](#frac_digits)|Devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha del separador decimal.|
|[grouping](#grouping)|Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.|
|[neg_format](#neg_format)|Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.|
|[negative_sign](#negative_sign)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.|
|[pos_format](#pos_format)|Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.|
|[positive_sign](#positive_sign)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.|
|[thousands_sep](#thousands_sep)|Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador de miles.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> moneypunct::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="curr_symbol"></a> moneypunct::curr_symbol

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene el símbolo de moneda.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_curr_symbol](#do_curr_symbol).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="decimal_point"></a> moneypunct::decimal_point

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como separador decimal.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como un símbolo de separador decimal.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="do_curr_symbol"></a> moneypunct::do_curr_symbol

Una función miembro virtual protegida que devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de moneda.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como un símbolo de separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [curr_symbol](#curr_symbol), donde `curr_symbol` llama a la función miembro virtual.

## <a name="do_decimal_point"></a> moneypunct::do_decimal_point

Una función miembro virtual protegida que devuelve una secuencia específica de la configuración regional de los elementos que se usan como un símbolo de separador decimal.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como un símbolo de separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [decimal_point](#decimal_point), donde `decimal_point` llama a la función miembro virtual.

## <a name="do_frac_digits"></a> moneypunct::do_frac_digits

Una función miembro virtual protegida que devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha de cualquier separador decimal.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha del separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [frac_digits](#frac_digits), donde `frac_digits` llama a la función miembro virtual.

## <a name="do_grouping"></a> moneypunct::do_grouping

Una función miembro virtual protegida que devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Valor devuelto

Una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [agrupación](#grouping), donde se llamó la función miembro virtual `grouping`.

## <a name="do_neg_format"></a> moneypunct::do_neg_format

Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Valor devuelto

La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo generar un campo de salida monetario para una cantidad negativa. Cada uno de los cuatro elementos de `pattern::field` puede tener los valores:

- `none` Para hacer coincidir cero o más espacios o generar nada.

- `sign` para buscar o generar un signo positivo o negativo.

- `space` Para hacer coincidir cero o más espacios o generar un espacio.

- `symbol` para buscar o generar un símbolo de moneda.

- `value` para buscar o generar un valor monetario.

Se generan los componentes de un campo de salida monetario y los componentes de un campo de entrada monetario se hacen coincidir en el orden en que estos elementos aparecen en `pattern::field`. Cada uno de los valores `sign`, `symbol`, `value`y `none` o `space` deben aparecer exactamente una vez. El valor `none` no debe aparecer en primer lugar. El espacio de valor **must** no debe aparecer en primer ni en último lugar. Si `Intl` es true, el orden es `symbol`, `sign`, `none`, a continuación, `value`.

La versión de plantilla de `moneypunct`\< **CharType**, **Intl**> devuelve `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [neg_format](#neg_format), donde `neg_format` llama a la función miembro virtual.

## <a name="do_negative_sign"></a> moneypunct::do_negative_sign

Una función miembro virtual protegida a la que se llama para devolver una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como signo negativo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [negative_sign](#negative_sign), donde `negative_sign` llama a la función miembro virtual.

## <a name="do_pos_format"></a> moneypunct::do_pos_format

Una función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Valor devuelto

La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo generar un campo de salida monetario para una cantidad positiva. (También determina cómo hacer coincidir los componentes de un campo de entrada monetario). La codificación es la misma que para [do_neg_format](#do_neg_format).

La versión de plantilla de moneypunct\< **CharType**, **Inputlterator**> devuelve `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [pos_format](#pos_format), donde `pos_format` llama a la función miembro virtual.

## <a name="do_positive_sign"></a> moneypunct::do_positive_sign

Una función miembro virtual protegida que devuelve una secuencia específica de la configuración regional de los elementos que se usan como signo positivo.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como signo positivo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [positive_sign](#positive_sign), donde `positive_sign` llama a la función miembro virtual.

## <a name="do_thousands_sep"></a> moneypunct::do_thousands_sep

Una función miembro virtual protegida que devuelve un elemento específico de la configuración regional que se va a usar como un separador de grupo a la izquierda de cualquier separador decimal.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Valor devuelto

Un elemento específico de la configuración regional que se va a usar como un separador de grupo a la izquierda de cualquier separador decimal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [thousands_sep](#thousands_sep), donde `thousands_sep` llama a la función miembro virtual.

## <a name="frac_digits"></a> moneypunct::frac_digits

Devuelve un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha del separador decimal.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento específico de la configuración regional de la cantidad de dígitos que se muestran a la derecha del separador decimal.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_frac_digits](#do_frac_digits).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="grouping"></a> moneypunct::grouping

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
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunct"></a> moneypunct::moneypunct

Constructor de objetos de tipo `moneypunct`.

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*<br/>
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles de la *_Refs* parámetro y su importancia son:

- 0: La vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: La duración del objeto debe administrarse manualmente.

- \> 1: Estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="neg_format"></a> moneypunct::neg_format

Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Valor devuelto

Una regla específica de la configuración regional para dar formato a resultados con cantidades negativas.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_neg_format](#do_neg_format).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="negative_sign"></a> moneypunct::negative_sign

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo negativo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_negative_sign](#do_negative_sign).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="pos_format"></a> moneypunct::pos_format

Devuelve una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Valor devuelto

Una regla específica de la configuración regional para dar formato a resultados con cantidades positivas.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_pos_format](#do_pos_format).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="positive_sign"></a> moneypunct::positive_sign

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como símbolo de signo positivo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_positive_sign](#do_positive_sign).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="string_type"></a> moneypunct::string_type

Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de puntuación.

## <a name="thousands_sep"></a> moneypunct::thousands_sep

Devuelve una secuencia específica de la configuración regional de los elementos que se usan como símbolo de separador de miles.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Valor devuelto

Una secuencia específica de la configuración regional de los elementos que se usan como separador de miles.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Ejemplo

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
