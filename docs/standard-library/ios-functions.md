---
title: Funciones de &lt;ios&gt;
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: c3b1e2350d0923cbfddf95492842ae126859e29f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426934"
---
# <a name="ltiosgt-functions"></a>Funciones de &lt;ios&gt;

## <a name="boolalpha"></a>boolalpha

Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como **True** o **False** en el flujo.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, las variables de tipo **bool** se muestran como 1 o 0.

`boolalpha` llama eficazmente a `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::boolalpha`) y, a continuación, devuelve *Str*.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) invierte el efecto de `boolalpha`.

### <a name="example"></a>Ejemplo

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a>Dec

Especifica que las variables de entero aparezcan en notación de base 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, las variables de entero se muestran en base 10.

`dec` llama eficazmente a `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::dec`, `ios_base::basefield`) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ios_defaultfloat"></a>&lt;iOS&gt; defaultfloat

Configura los indicadores de un objeto `ios_base` para que utilicen un formato de presentación predeterminado para valores float.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parámetros

*_Iosbase*\
Objeto `ios_base`.

### <a name="remarks"></a>Observaciones

El manipulador llama eficazmente `iosbase.`[ios_base:: unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`y, a continuación, devuelve *iosbase*.

## <a name="fixed"></a>resuelto

Especifica que un número de punto flotante se muestre en notación de decimal fijo.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

`fixed` es la notación de presentación predeterminada para los números de punto flotante. [scientific](../standard-library/ios-functions.md#scientific) hace que los números de punto flotante se muestren con notación científica.

El manipulador llama eficazmente a *Str*. [setf](../standard-library/ios-base-class.md#setf)(`ios_base::fixed`, `ios_base::floatfield`) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a>hueca

Especifica que las variables de entero aparezcan en notación de base 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, las variables de entero se muestran en notación de base 10. [dec](../standard-library/ios-functions.md#dec) y [oct](../standard-library/ios-functions.md#oct) también cambian la forma en que aparecen las variables de entero.

El manipulador llama eficazmente a `str` **.** [setf](../standard-library/ios-base-class.md#setf)(`ios_base::hex`, `ios_base::basefield`) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [Dec](../standard-library/ios-functions.md#dec) para obtener un ejemplo de cómo usar `hex`.

## <a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a>nivel

Hace que el signo de un número esté justificado a la izquierda y el número se alinee a la derecha.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

[showpos](../standard-library/ios-functions.md#showpos) hace que se muestre el signo de los números positivos.

El manipulador llama eficazmente a `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: Internal](../standard-library/ios-base-class.md#fmtflags)`, `[ios_base:: adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a>salido

Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen izquierdo.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

El manipulador llama eficazmente `str.``(ios_base::left, ios_base::adjustfield)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
5
        5
```

## <a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a>noboolalpha

Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como 1 o 0 en el flujo.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, `noboolalpha` está en vigor.

`noboolalpha` llama eficazmente a `str.``(ios_base::boolalpha)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) invierte el efecto de `noboolalpha`.

### <a name="example"></a>Ejemplo

Vea [boolalpha](../standard-library/ios-functions.md#boolalpha) para obtener un ejemplo que usa `noboolalpha`.

## <a name="noshowbase"></a>noshowbase

Desactiva la opción que indica la base notacional en que se muestra un número.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

`noshowbase` está activado. Use [showbase](../standard-library/ios-functions.md#showbase) para indicar la base notacional de los números.

El manipulador llama eficazmente `str.``(ios_base::showbase)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [showbase](../standard-library/ios-functions.md#showbase) para obtener un ejemplo de cómo usar `noshowbase`.

## <a name="noshowpoint"></a>noshowpoint

Muestra solo la parte de número entero en los números de punto flotante cuya parte fraccionaria es cero.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

`noshowpoint` está activado de forma predeterminada; use [showpoint](../standard-library/ios-functions.md#showpoint) y [precision](../standard-library/ios-base-class.md#precision) para mostrar ceros después del punto decimal.

El manipulador llama eficazmente `str.``(ios_base::showpoint)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a>noshowpos

Hace que los números positivos no tengan signo explícito.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

`noshowpos` está activado.

El manipulador llama eficazmente `str.``(ios_base::showps)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [showpos](../standard-library/ios-functions.md#showpos) para obtener un ejemplo que usa `noshowpos`.

## <a name="noskipws"></a>noskipws

Hace que el flujo de entrada lea los espacios.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, [skipws](../standard-library/ios-functions.md#skipws) está en vigor. Cuando se lee un espacio en el flujo de entrada, señala el final del búfer.

El manipulador llama eficazmente `str.``(ios_base::skipws)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a>nounitbuf

Hace que la salida se almacene en búfer y se procese cuando el búfer esté lleno.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

[unitbuf](../standard-library/ios-functions.md#unitbuf) hace que el búfer se procese cuando no está vacío.

El manipulador llama eficazmente `str.``(ios_base::unitbuf)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

## <a name="nouppercase"></a>nouppercase

Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en minúscula.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

El manipulador llama eficazmente `str.``(ios_base::uppercase)`[unsetf](../standard-library/ios-base-class.md#unsetf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [uppercase](../standard-library/ios-functions.md#uppercase) para obtener un ejemplo que usa `nouppercase`.

## <a name="oct"></a>Octubre

Especifica que las variables de entero aparezcan en notación de base 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, las variables de entero se muestran en notación de base 10. [dec](../standard-library/ios-functions.md#dec) y [hex](../standard-library/ios-functions.md#hex) también cambian la forma en que aparecen las variables de entero.

El manipulador llama eficazmente `str.``(ios_base::oct, ios_base::basefield)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [Dec](../standard-library/ios-functions.md#dec) para obtener un ejemplo de cómo usar `oct`.

## <a name="right"></a>correcta

Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen derecho.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

[left](../standard-library/ios-functions.md#left) también modifica la justificación del texto.

El manipulador llama eficazmente `str.``(ios_base::right, ios_base::adjustfield)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a>Ciencia

Hace que los números de punto flotante se muestren con notación científica.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, la notación [fixed](../standard-library/ios-functions.md#fixed) está en vigor para los números de punto flotante.

El manipulador llama eficazmente `str.``(ios_base::scientific, ios_base::floatfield)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a>showbase

Indica la base notacional en que se muestra un número.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

La base notacional de un número puede cambiarse por [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) o [hex](../standard-library/ios-functions.md#hex).

El manipulador llama eficazmente `str.``(ios_base::showbase)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a>showpoint

Muestra la parte de número entero de un número de punto flotante y los dígitos que hay a la derecha del separador decimal, incluso cuando la parte fraccionaria es cero.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, [noshowpoint](../standard-library/ios-functions.md#noshowpoint) está en vigor.

El manipulador llama eficazmente `str.``(ios_base::showpoint)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

Vea [noshowpoint](../standard-library/ios-functions.md#noshowpoint) para obtener un ejemplo que usa `showpoint`.

## <a name="showpos"></a>showpos

Hace que los números positivos tengan signo explícito.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

[noshowpos](../standard-library/ios-functions.md#noshowpos) es el valor predeterminado.

El manipulador llama eficazmente `str.``(ios_base::showpos)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a>skipws

Hace que el flujo de entrada no lea los espacios.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, `skipws` está en vigor. [noskipws](../standard-library/ios-functions.md#noskipws) hace que se lean los espacios del flujo de entrada.

El manipulador llama eficazmente `str.``(ios_base::skipws)`[setf](../standard-library/ios-base-class.md#setf) y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a>unitbuf

Hace que la salida se procese cuando el búfer no está lleno.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `endl` también vacía el búfer.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) está en vigor de forma predeterminada.

El manipulador llama eficazmente a `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`y, a continuación, devuelve *Str*.

## <a name="uppercase"></a>  uppercase

Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en mayúscula.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Referencia a un objeto de tipo [ios_base](../standard-library/ios-base-class.md) o a un tipo que hereda de `ios_base`.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto del que se deriva *Str* .

### <a name="remarks"></a>Observaciones

De forma predeterminada, [nouppercase](../standard-library/ios-functions.md#nouppercase) está en vigor.

El manipulador llama eficazmente a `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: Uppercase](../standard-library/ios-base-class.md#fmtflags)`)`y, a continuación, devuelve *Str*.

### <a name="example"></a>Ejemplo

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```
