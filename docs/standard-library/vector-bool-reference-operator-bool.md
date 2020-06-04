---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: ca2d21a7706248cd84ca3591eb717e4081972f9c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452121"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Proporciona una conversión implícita de `vector<bool>::reference` a **bool**.

## <a name="syntax"></a>Sintaxis

```cpp
operator bool() const;
```

## <a name="return-value"></a>Valor devuelto

El valor booleano del elemento del objeto [vector\<bool>](../standard-library/vector-bool-class.md).

## <a name="remarks"></a>Comentarios

Este operador no puede modificar el objeto `vector<bool>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[vector\<bool>::reference (Clase)](../standard-library/vector-bool-reference-class.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
