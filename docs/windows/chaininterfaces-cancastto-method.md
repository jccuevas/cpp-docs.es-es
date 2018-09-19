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
ms.openlocfilehash: 8398f0bd4d9fdc786926782b13ebcac913a6a351
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612875"
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

*riid*  
Id. de interfaz.

*PPV*  
Un puntero en el último identificador de interfaz que se convirtió correctamente.

## <a name="return-value"></a>Valor devuelto

**True** si todas las operaciones de conversión se realizó correctamente; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)