---
title: Funciones &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363077"
---
# <a name="ltistreamgt-functions"></a>Funciones &lt;istream&gt;

|||
|-|-|
|[swap](#istream_swap)|[Ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>Intercambio

Intercambia los elementos de dos objetos stream.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Flujo.

*Correcto*\
Flujo.

## <a name="ws"></a><a name="ws"></a>Ws

Omite los espacios en blanco en el flujo.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parámetros

*_Istr*\
Flujo.

### <a name="return-value"></a>Valor devuelto

Flujo.

### <a name="remarks"></a>Observaciones

El manipulador extrae y `ch` descarta cualquier elemento para el que [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) sea true.

La función llama a [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si encuentra el final del archivo al extraer elementos. Devuelve *_Istr*.

### <a name="example"></a>Ejemplo

Vea [operator>>](../standard-library/istream-operators.md#op_gt_gt) para obtener un ejemplo que usa `ws`.

## <a name="see-also"></a>Consulte también

[\<>istream](../standard-library/istream.md)
