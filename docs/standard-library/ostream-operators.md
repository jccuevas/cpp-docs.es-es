---
title: Operadores &lt;ostream&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ostream/std::operator&lt;&lt;
dev_langs:
- C++
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4819f5b5d5d6a16720bce29dd176fd0eb873014a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955938"
---
# <a name="ltostreamgt-operators"></a>Operadores &lt;ostream&gt;

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a> operator&lt;&lt;

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

*_Ch* un carácter.

*_Elem* el tipo de elemento.

*_Ostr* A `basic_ostream` objeto.

*Str* una cadena de caracteres.

*_Tr* rasgos de caracteres.

*Val* el tipo

### <a name="return-value"></a>Valor devuelto

La secuencia.

### <a name="remarks"></a>Comentarios

La clase `basic_ostream` también define varios operadores de inserción. Para obtener más información, vea [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

La función de plantilla

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Determina la longitud N = `traits_type::` [longitud](../standard-library/char-traits-struct.md#length)(`str`) de la secuencia que comienza por *str*e inserta la secuencia. Si N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), entonces la función también inserta una repetición de `_Ostr.width` - N caracteres de relleno. La repetición precede la secuencia si (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left). De otro modo, la repetición sigue la secuencia. La función devuelve *_Ostr*.

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

excepto en que cada elemento *_Ch* de la secuencia que comienza por *str* se convierte en un objeto de tipo `Elem` mediante una llamada a `_Ostr.` [colocar](../standard-library/basic-ostream-class.md#put)(`_Ostr.` [widen](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

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

salvo que *_Ch* se convierte en un objeto de tipo `Elem` mediante una llamada a `_Ostr.put`( `_Ostr.widen`( `_Ch`)).

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

Devuelve `_Ostr` << (`const char *`) `str`.

La función de plantilla

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Devuelve `_Ostr` << (`char`) `_Ch`.

La función de plantilla:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Devuelve `_Ostr` << (`const char *`) `str`.

La función de plantilla:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Devuelve `_Ostr` << (`char`) `_Ch`.

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

## <a name="see-also"></a>Vea también

[\<ostream>](../standard-library/ostream.md)<br/>
