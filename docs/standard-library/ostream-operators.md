---
title: Operadores &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: d8b6f4e0f0b5bca41f8d895415fff4003231ad1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373602"
---
# <a name="ltostreamgt-operators"></a>Operadores &lt;ostream&gt;

||
|-|
|[Operador&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operador&lt;&lt;

Escribe varios tipos en la secuencia.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Parámetros

*_Ch*\
Un carácter.

*_Elem*\
El tipo de elemento.

*_Ostr*\
Objeto `basic_ostream` .

*Str*\
Una cadena de caracteres.

*_Tr*\
Rasgos de los caracteres.

*Val*\
El tipo

### <a name="return-value"></a>Valor devuelto

Flujo.

### <a name="remarks"></a>Observaciones

La clase `basic_ostream` también define varios operadores de inserción. Para obtener más información, consulte [basic_ostream::operator&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

La función de plantilla

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

determina la longitud `traits_type::`N`str`- [longitud](../standard-library/char-traits-struct.md#length)( ) de la secuencia que comienza en *str*, e inserta la secuencia. Si N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), entonces la función también inserta una repetición de `_Ostr.width` - N caracteres de relleno. La repetición precede a`_Ostr`la secuencia si ( . [banderas](../standard-library/ios-base-class.md#flags)  &  `adjustfield` !- [izquierda](../standard-library/ios-functions.md#left). De otro modo, la repetición sigue la secuencia. La función devuelve *_Ostr*.

La función de plantilla

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

inserta el elemento `_Ch`. Si 1 < `_Ostr.width`, entonces la función también inserta una repetición de `_Ostr.width` - 1 caracteres de relleno. La repetición precede la secuencia si `_Ostr.flags & adjustfield != left`. De otro modo, la repetición sigue la secuencia. Devuelve *_Ostr*.

La función de plantilla

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

se comporta igual que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

excepto que cada elemento *_Ch* de la secuencia que comienza `Elem` en `_Ostr.` *str* se`_Ch`convierte en un objeto de tipo llamando a [put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[widen](../standard-library/basic-ios-class.md#widen)( )).

La función de plantilla

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

se comporta igual que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

excepto que *_Ch* se convierte `Elem` en `_Ostr.put`un `_Ostr.widen` `_Ch`objeto de tipo llamando a ( ( ( )).

La función de plantilla

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

se comporta igual que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(No tiene que ampliar los elementos antes de insertarlos).

La función de plantilla

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

se comporta igual que

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(No tiene que ampliar *_Ch* antes de insertarlo.)

La función de plantilla

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

devuelve `_Ostr` `const char *` << ( `str`) .

La función de plantilla

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

devuelve `_Ostr` `char` << ( `_Ch`) .

La función de plantilla:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

devuelve `_Ostr` `const char *` << ( `str`) .

La función de plantilla:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

devuelve `_Ostr` `char` << ( `_Ch`) .

La función de plantilla:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

devuelve `_Ostr` `<<` `val` (y convierte una [referencia a un valor R](../cpp/rvalue-reference-declarator-amp-amp.md) para `_Ostr` en un valor L en el proceso).

### <a name="example"></a>Ejemplo

Vea [flush](../standard-library/ostream-functions.md#flush) para obtener un ejemplo que usa `operator<<`.

## <a name="see-also"></a>Consulte también

[\<>ostream](../standard-library/ostream.md)
