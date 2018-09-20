---
title: Método Chaininterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 752c3598a38117506154b0a2b7d7d3e578bf3c3e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417649"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo (Método)

Indica si el identificador de interfaz especificado puede convertirse a cada una de las especializaciones definidas por los parámetros de plantilla no predeterminado.

## <a name="syntax"></a>Sintaxis

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*PPV*<br/>
Un puntero en el último identificador de interfaz que se convirtió correctamente.

## <a name="return-value"></a>Valor devuelto

**True** si todas las operaciones de conversión se realizó correctamente; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)