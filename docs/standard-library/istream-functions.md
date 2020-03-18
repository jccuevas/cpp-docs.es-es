---
title: Funciones &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425686"
---
# <a name="ltistreamgt-functions"></a>Funciones &lt;istream&gt;

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a> swap

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

\ *izquierda*
Un flujo.

\ *derecha*
Un flujo.

## <a name="ws"></a>  ws

Omite los espacios en blanco en el flujo.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parámetros

*_Istr*\
Un flujo.

### <a name="return-value"></a>Valor devuelto

Flujo.

### <a name="remarks"></a>Observaciones

El manipulador extrae y descarta cualquier elemento `ch` para el que [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **es**( **ctype**\< **Elem**>:: **Space**, **CH**) es true.

La función llama a [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si encuentra el final del archivo al extraer elementos. Devuelve *_Istr*.

### <a name="example"></a>Ejemplo

Vea [operator>>](../standard-library/istream-operators.md#op_gt_gt) para obtener un ejemplo que usa `ws`.

## <a name="see-also"></a>Consulte también

[\<istream>](../standard-library/istream.md)
