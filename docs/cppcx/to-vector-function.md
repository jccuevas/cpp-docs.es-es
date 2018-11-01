---
title: to_vector (Función)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: a2054e6e787dcf9137a087dd53264c7f98461d69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508958"
---
# <a name="tovector-function"></a>to_vector (Función)

Devuelve un objeto `std::vector` cuyo valor es igual que la colección que subyace al parámetro de IVector o de IVectorView especificado.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El parámetro de tipo de plantilla.

*v*<br/>
Una interfaz IVector o IVectorView que proporciona acceso a un objeto Vector o VectorView subyacente.

### <a name="return-value"></a>Valor devuelto

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Windows::Foundation::Collections

## <a name="see-also"></a>Vea también

[Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)