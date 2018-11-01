---
title: Funciones de &lt;iomanip&gt;
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: 3df26de9ef485bc7214e49ce96680cc7300adb93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574332"
---
# <a name="ltiomanipgt-functions"></a>Funciones de &lt;iomanip&gt;

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[quoted](#quoted)|[resetiosflags](#resetiosflags)|
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|
|[setprecision](#setprecision)|[setw](#setw)|

## <a name="iomanip_get_money"></a>  get_money

Extrae un valor monetario de un flujo con el formato deseado y devuelve el valor en un parámetro.

```cpp
template <class Money>
T7 get_money(Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parámetros

*_Cantidad*<br/>
Valor monetario extraído.

*_Intl*<br/>
Si **true**, use el formato internacional. El valor predeterminado es **false**.

### <a name="remarks"></a>Comentarios

El manipulador devuelve un objeto que, cuando se extrae del flujo `str`, se comporta como un `formatted input function` que llama a la función miembro `get` para la faceta de configuración regional `money_get` asociado `str`con *_ Intl* para indicar el formato internacional. Si es correcto, la llamada almacena en *_cantidad* el valor monetario extraído. Después, el manipulador devuelve `str`.

`Money` debe ser de tipo `long double` o una instancia de `basic_string` con los mismos parámetros de elemento y rasgos que `str`.

## <a name="iomanip_get_time"></a>  get_time

Extrae un valor de tiempo de un flujo con el formato deseado. Devuelve el valor en un parámetro como una estructura de tiempo.

```cpp
template <class Elem>
T10 put_time(struct tm *_Tptr, const Elem *_Fmt);
```

### <a name="parameters"></a>Parámetros

*_Tptr*<br/>
Tiempo en forma de estructura de tiempo.

*_Fmt*<br/>
Formato que se quiere usar para obtener el valor de tiempo.

### <a name="remarks"></a>Comentarios

El manipulador devuelve un objeto que, cuando se extrae del flujo `str`, se comporta como una `formatted input function` que llama a la función miembro `get` para la faceta de configuración regional `time_get` asociada a `str`, con `tptr` para indicar la estructura de tiempo y `fmt` para indicar el comienzo de una cadena de formato terminada en null. Si es correcto, la llamada almacena en la estructura de tiempo los valores asociados a todos los campos de tiempo extraídos. Después, el manipulador devuelve `str`.

## <a name="iomanip_put_money"></a>  put_money

Inserta un importe monetario con el formato deseado en un flujo.

```cpp
template <class Money>
T8 put_money(const Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parámetros

*_Cantidad*<br/>
Importe monetario que se va a insertar en el flujo.

*_Intl*<br/>
Establecido en **true** si manipulador debe usar el formato internacional, **false** si no debe hacerlo.

### <a name="return-value"></a>Valor devuelto

Devuelve `str`.

### <a name="remarks"></a>Comentarios

El manipulador devuelve un objeto que, cuando se inserta en el flujo `str`, se comporta como una función de salida con formato que llama a la función miembro `put` para la faceta de configuración regional `money_put` asociada a `str`. Si es correcto, la llamada inserta `amount` con el formato adecuado, con * _Intl` to indicate international format and `str.fill()`, as the fill element. The manipulator then returns `str'.

`Money` debe ser de tipo `long double` o una instancia de `basic_string` con los mismos parámetros de elemento y rasgos que `str`.

## <a name="iomanip_put_time"></a>  put_time

Escribe un valor de tiempo de una estructura de tiempo en un flujo con el formato especificado.

```cpp
template <class Elem>
T10 put_time(struct tm* _Tptr, const Elem* _Fmt);
```

### <a name="parameters"></a>Parámetros

*_Tptr*<br/>
Valor de tiempo que se va a escribir en el flujo, proporcionado en una estructura de tiempo.

*_Fmt*<br/>
Formato deseado para escribir el valor de tiempo.

### <a name="remarks"></a>Comentarios

El manipulador devuelve un objeto que, cuando se inserta en el flujo `str`, se comporta como una `formatted output function`. La función de salida llama a la función miembro `put` para la faceta de configuración regional `time_put` asociada a `str`. Usa la función de salida *_Tptr* para indicar la estructura de tiempo y *_Fmt* para indicar el comienzo de una cadena de formato terminada en null. Si es correcto, la llamada inserta texto literal de la cadena de formato y valores convertidos de la estructura de tiempo. Después, el manipulador devuelve `str`.

## <a name="quoted"></a>  quoted

**(Nuevo en C++14)** Manipulador de iostream que permite realizar un práctico recorrido de ida y vuelta de cadenas dentro y fuera de flujos mediante los operadores >> y <<.

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Un std:: String, char\*, una cadena literal de cadena sin formato o literal o una versión ancha de cualquiera de estos (por ejemplo, std:: wstring, wchar_t\*).

*Delimitador*<br/>
Un carácter especificado por el usuario o carácter ancho, que se utilizará como delimitador para el principio y el final de la cadena.

*escape*<br/>
Un carácter especificado por el usuario o carácter ancho, que se utilizará como carácter de escape para las secuencias de escape dentro de la cadena.

### <a name="remarks"></a>Comentarios

Vea [Usar operadores de inserción y controlar el formato](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Ejemplo

Este ejemplo muestra cómo utilizar `quoted` con el carácter de delimitador y de escape predeterminados mediante cadenas estrechas. También se admiten las cadenas anchas.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_quoted_v_nonquoted()
{
    // Results are identical regardless of input string type:
    // string inserted { R"(This is a "sentence".)" }; // raw string literal
    // string inserted { "This is a \"sentence\"." };  // regular string literal
    const char* inserted = "This is a \"sentence\".";  // const char*
    stringstream ss, ss_quoted;
    string extracted, extracted_quoted;

    ss << inserted;
    ss_quoted << quoted(inserted);

    cout << "ss.str() is storing       : " << ss.str() << endl;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;

    // Round-trip the strings
    ss >> extracted;
    ss_quoted >> quoted(extracted_quoted);

    cout << "After round trip: " << endl;
    cout << "Non-quoted      : " << extracted << endl;
    cout << "Quoted          : " << extracted_quoted << endl;
}

void main(int argc, char* argv[])
{
    show_quoted_v_nonquoted();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}

/* Output:
ss.str() is storing       : This is a "sentence".
ss_quoted.str() is storing: "This is a \"sentence\"."

After round trip:
Non-quoted      : This
Quoted          : This is a "sentence".

Press Enter to exit
*/
```

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo proporcionar un carácter de delimitador o de escape personalizado:

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_custom_delimiter()
{
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    stringstream ss, ss_quoted;
    string extracted;

    ss_quoted << quoted(inserted, '*');
    ss << inserted;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;

    // Use the same quoted arguments as on insertion.
    ss_quoted >> quoted(extracted, '*');

    cout << "After round trip: " << endl;
    cout << "Quoted          : " << extracted << endl;

    extracted = {};
    ss >> extracted;
    cout << "Non-quoted      : " << extracted << endl << endl;
}

void show_custom_escape()
{
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };
    stringstream ss, ss_quoted, ss_quoted_custom;
    string extracted;

    // Use '"' as delimiter and '~' as escape character.
    ss_quoted_custom << quoted(inserted, '"', '~');
    ss_quoted << quoted(inserted);
    ss << inserted;
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;
    cout << "ss.str()              : " << ss.str() << endl << endl;

    // No spaces in this string, so non-quoted behaves same as quoted
    // after round-tripping.
}

void main(int argc, char* argv[])
{
    cout << "Custom delimiter:" << endl;
    show_custom_delimiter();
    cout << "Custom escape character:" << endl;
    show_custom_escape();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}
/* Output:
Custom delimiter:
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".

After round trip:
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".
Non-quoted      : "This"

Custom escape character:
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"
ss.str()              : \\root\trunk\branch\nest\egg\yolk

Press Enter to exit
*/

```

## <a name="resetiosflags"></a>  resetiosflags

Borra las marcas especificadas.

```cpp
T1 resetiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parámetros

*Máscara*<br/>
Marcas que se van a borrar.

### <a name="return-value"></a>Valor devuelto

El manipulador devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags), _ *máscara*) y, a continuación, devuelve `str`.

### <a name="example"></a>Ejemplo

Vea [setw](../standard-library/iomanip-functions.md#setw) para obtener un ejemplo que usa `resetiosflags`.

## <a name="setbase"></a>  setbase

Establece la base de los enteros.

```cpp
T3 setbase(int _Base);
```

### <a name="parameters"></a>Parámetros

*_Base*<br/>
Base numérica.

### <a name="return-value"></a>Valor devuelto

El manipulador devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. `setf`( **máscara**, [ios_base:: basefield](../standard-library/ios-base-class.md#fmtflags)) y, a continuación, devuelve `str`. En este caso, `mask` se determina como sigue:

- Si _ *Base* es 8, a continuación, `mask` es `ios_base::` [oct](../standard-library/ios-functions.md#oct).

- Si _ *Base* es 10, mask es `ios_base::`[dec](../standard-library/ios-functions.md#dec).

- Si _ *Base* es 16, `mask` es `ios_base::` [hexadecimal](../standard-library/ios-functions.md#hex).

- Si _ *Base* es cualquier otro valor, mask es `ios_base::`[fmtflags](../standard-library/ios-base-class.md#fmtflags)(0).

### <a name="example"></a>Ejemplo

Vea [setw](../standard-library/iomanip-functions.md#setw) para obtener un ejemplo que usa `setbase`.

## <a name="setfill"></a>  setfill

Establece el carácter que se usará para rellenar los espacios en una presentación justificada a la derecha.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Parámetros

*CH*<br/>
Carácter que se usará para rellenar los espacios en una presentación justificada a la derecha.

### <a name="return-value"></a>Valor devuelto

El manipulador de la plantilla devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. [relleno](../standard-library/basic-ios-class.md#fill)(`Ch`) y, a continuación, devuelve `str`. El tipo `Elem` debe ser el mismo que el tipo de elemento de la secuencia `str`.

### <a name="example"></a>Ejemplo

Vea [setw](../standard-library/iomanip-functions.md#setw) para obtener un ejemplo que usa `setfill`.

## <a name="setiosflags"></a>  setiosflags

Establece las marcas especificadas.

```cpp
T2 setiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parámetros

*Máscara*<br/>
Marcas que se van a establecer.

### <a name="return-value"></a>Valor devuelto

El manipulador devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. [SETF](../standard-library/ios-base-class.md#setf)(_ *máscara*) y, a continuación, devuelve `str`.

### <a name="example"></a>Ejemplo

Vea [setw](../standard-library/iomanip-functions.md#setw) para obtener un ejemplo que usa `setiosflags`.

## <a name="setprecision"></a>  setprecision

Establece la precisión de los valores de punto flotante.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Parámetros

*Prec*<br/>
Precisión de los valores de punto flotante.

### <a name="return-value"></a>Valor devuelto

El manipulador devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. [precisión](../standard-library/ios-base-class.md#precision)(`Prec`) y, a continuación, devuelve `str`.

### <a name="example"></a>Ejemplo

Vea [setw](../standard-library/iomanip-functions.md#setw) para obtener un ejemplo que usa `setprecision`.

## <a name="setw"></a>  setw

Especifica el ancho del campo de presentación para el siguiente elemento del flujo.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Parámetros

*Amplia*<br/>
Ancho del campo de presentación.

### <a name="return-value"></a>Valor devuelto

El manipulador devuelve un objeto que, cuando se extraen o se inserta en la secuencia `str`, llamadas **str**. [ancho](../standard-library/ios-base-class.md#width)(_ *amplia*), a continuación, devuelve `str`.

### <a name="remarks"></a>Comentarios

setw establece el ancho solo para el siguiente elemento del flujo y se debe insertar delante de cada elemento cuyo ancho se desea especificar.

### <a name="example"></a>Ejemplo

```cpp
// iomanip_setw.cpp
// compile with: /EHsc
// Defines the entry point for the console application.
//
// Sample use of the following manipulators:
//   resetiosflags
//   setiosflags
//   setbase
//   setfill
//   setprecision
//   setw

#include <iostream>
#include <iomanip>

using namespace std;

const double   d1 = 1.23456789;
const double   d2 = 12.3456789;
const double   d3 = 123.456789;
const double   d4 = 1234.56789;
const double   d5 = 12345.6789;
const long      l1 = 16;
const long      l2 = 256;
const long      l3 = 1024;
const long      l4 = 4096;
const long      l5 = 65536;
int         base = 10;

void DisplayDefault( )
{
   cout << endl << "default display" << endl;
   cout << "d1 = " << d1 << endl;
   cout << "d2 = " << d2 << endl;
   cout << "d3 = " << d3 << endl;
   cout << "d4 = " << d4 << endl;
   cout << "d5 = " << d5 << endl;
}

void DisplayWidth( int n )
{
   cout << endl << "fixed width display set to " << n << ".\n";
   cout << "d1 = " << setw(n) << d1 << endl;
   cout << "d2 = " << setw(n) << d2 << endl;
   cout << "d3 = " << setw(n) << d3 << endl;
   cout << "d4 = " << setw(n) << d4 << endl;
   cout << "d5 = " << setw(n) << d5 << endl;
}

void DisplayLongs( )
{
   cout << setbase(10);
   cout << endl << "setbase(" << base << ")" << endl;
   cout << setbase(base);
   cout << "l1 = " << l1 << endl;
   cout << "l2 = " << l2 << endl;
   cout << "l3 = " << l3 << endl;
   cout << "l4 = " << l4 << endl;
   cout << "l5 = " << l5 << endl;
}

int main( int argc, char* argv[] )
{
   DisplayDefault( );

   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);
   DisplayDefault( );

   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);
   DisplayDefault( );

   cout << setiosflags(ios_base::scientific);
   cout << endl << "setiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << resetiosflags(ios_base::scientific);
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << endl << "setfill('" << 'S' << "')" << setfill('S');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);
   DisplayWidth(10);
   DisplayDefault( );

   base = 16;
   DisplayLongs( );

   base = 8;
   DisplayLongs( );

   base = 10;
   DisplayLongs( );

   return   0;
}
```

```Output

default display
d1 = 1.23457
d2 = 12.3457
d3 = 123.457
d4 = 1234.57
d5 = 12345.7

setprecision(3)
default display
d1 = 1.23
d2 = 12.3
d3 = 123
d4 = 1.23e+003
d5 = 1.23e+004

setprecision(12)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setiosflags(4096)
default display
d1 = 1.234567890000e+000
d2 = 1.234567890000e+001
d3 = 1.234567890000e+002
d4 = 1.234567890000e+003
d5 = 1.234567890000e+004

resetiosflags(4096)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill('S')
fixed width display set to 15.
d1 = SSSSS1.23456789
d2 = SSSSS12.3456789
d3 = SSSSS123.456789
d4 = SSSSS1234.56789
d5 = SSSSS12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill(' ')
fixed width display set to 15.
d1 =      1.23456789
d2 =      12.3456789
d3 =      123.456789
d4 =      1234.56789
d5 =      12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setprecision(8)
fixed width display set to 10.
d1 =  1.2345679
d2 =  12.345679
d3 =  123.45679
d4 =  1234.5679
d5 =  12345.679

default display
d1 = 1.2345679
d2 = 12.345679
d3 = 123.45679
d4 = 1234.5679
d5 = 12345.679

setbase(16)
l1 = 10
l2 = 100
l3 = 400
l4 = 1000
l5 = 10000

setbase(8)
l1 = 20
l2 = 400
l3 = 2000
l4 = 10000
l5 = 200000

setbase(10)
l1 = 16
l2 = 256
l3 = 1024
l4 = 4096
l5 = 65536
```

## <a name="see-also"></a>Vea también

[\<iomanip>](../standard-library/iomanip.md)<br/>
