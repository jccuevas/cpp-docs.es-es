---
title: Método Implementshelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 9ae6fa17-d0b1-4e31-9ae5-da6ae4026e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9487ba4e05a0094d852b0db0c9c39009c027dc9e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423746"
---
# <a name="implementshelpercancastto-method"></a>ImplementsHelper::CanCastTo (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Referencia a un identificador de interfaz.

*PPV*<br/>
Si esta operación se realiza correctamente, un puntero a la interfaz especificada por *riid* o *iid*.

*IID*<br/>
Referencia a un identificador de interfaz.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Obtiene un puntero al identificador de interfaz especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[ImplementsHelper (estructura)](../windows/implementshelper-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)