---
title: Operadores &lt;bitset&gt;
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: cd1dfc035fde06c4be0f90e1bd11b231d64ab811
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890137"
---
# <a name="ltbitsetgt-operators"></a>Operadores &lt;bitset&gt;

## <a name="op_amp"></a> operator&amp;

Efectúa una operación bit a bit `AND` entre dos conjuntos de bits.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
El primero de los dos conjuntos de bits cuyos elementos respectivos van a combinarse con la operación bit a bit `AND`.

\ *derecha*
El segundo de los dos valarrays cuyos elementos respectivos van a combinarse con la operación bit a bit `AND`.

### <a name="return-value"></a>Valor devuelto

Una BitSet cuyos elementos son el resultado de realizar la operación de `AND` en los elementos correspondientes de *izquierda* y *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a>operador&lt;&lt;

Inserta una representación de texto de la secuencia de bits en el flujo de salida.

```
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Un objeto de tipo **bitset\<N>** que se va a insertar en el flujo de salida como una cadena.

### <a name="return-value"></a>Valor devuelto

Representación de texto de la secuencia de bits en `ostr`.

### <a name="remarks"></a>Comentarios

La función de plantilla sobrecarga `operator<<`, lo que permite escribir una BitSet sin convertirla primero en una cadena. La función de plantilla ejecuta eficazmente:

`ostr << right.`[to_string](bitset-class.md)`<CharType, Traits, allocator<CharType>>()`

### <a name="example"></a>Ejemplo

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a>operador&gt;&gt;

Lee una cadena de caracteres de bit en un conjunto de bits.

```
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& i_str,
    bitset<N>& right);
```

### <a name="parameters"></a>Parámetros

\ *i_str*
La cadena que se escribe en el flujo de entrada para insertarla en un conjunto de bits.

\ *derecha*
El conjunto de bits que recibe los bits del flujo de entrada.

### <a name="return-value"></a>Valor devuelto

La función de plantilla devuelve la cadena *i_str*.

### <a name="remarks"></a>Comentarios

La función de plantilla sobrecarga `operator>>` para almacenar en la *parte derecha* el valor `bitset(str)`, donde `str` es un objeto de tipo [basic_string](basic-string-class.md)`< CharType, Traits, allocator< CharType > >&` extraído de *i_str*.

La función de plantilla extrae los elementos de *i_str* y los inserta en el BitSet hasta que:

- Todos los elementos de bits se han extraído del flujo de entrada y se almacenan en el conjunto de bits.

- El conjunto de bits se llena con bits del flujo de entrada.

- Se encuentra un elemento de entrada que no es 0 ni 1.

### <a name="example"></a>Ejemplo

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a>operador ^

Efectúa una operación bit a bit `EXCLUSIVE-OR` entre dos conjuntos de bits.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
El primero de los dos conjuntos de bits cuyos elementos respectivos van a combinarse con la operación bit a bit `EXCLUSIVE-OR`.

\ *derecha*
El segundo de los dos valarrays cuyos elementos respectivos van a combinarse con la operación bit a bit `EXCLUSIVE-OR`.

### <a name="return-value"></a>Valor devuelto

Una BitSet cuyos elementos son el resultado de realizar la operación de `EXCLUSIVE-OR` en los elementos correspondientes de *izquierda* y *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a>Operator&#124;

Efectúa una operación bit a bit `OR` entre dos conjuntos de bits.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
El primero de los dos conjuntos de bits cuyos elementos respectivos van a combinarse con la operación bit a bit `OR`.

\ *derecha*
El segundo de los dos valarrays cuyos elementos respectivos van a combinarse con la operación bit a bit `OR`.

### <a name="return-value"></a>Valor devuelto

Una BitSet cuyos elementos son el resultado de realizar la operación de `OR` en los elementos correspondientes de *izquierda* y *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
