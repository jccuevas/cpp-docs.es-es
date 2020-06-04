---
title: back_inserter (Función)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209447"
---
# <a name="backinserter-function"></a>back_inserter (Función)

Devuelve un iterador que se utiliza para insertar elementos en el final de la colección especificada.

## <a name="syntax"></a>Sintaxis

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un parámetro de tipo de plantilla.

*v*<br/>
Un puntero de interfaz que proporciona acceso a la colección subyacente.

### <a name="return-value"></a>Valor devuelto

Iterador.

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Windows::Foundation::Collections

## <a name="see-also"></a>Vea también

[Windows::Foundation::Collections (Espacio de nombres)](../cppcx/windows-foundation-collections-namespace-c-cx.md)
