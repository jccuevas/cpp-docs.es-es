---
title: Método Runtimeclass | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3c16d54b08d0c687b33381107eb17be351e9d6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589487"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids (Método)

Obtiene una matriz que puede contener la interfaz implementadas por la actual de identificadores **RuntimeClass** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   GetIids
)  
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parámetros

*iidCount*  
Cuando finalice esta operación, el número total de elementos de matriz *IID*.

*IID*  
Cuando se completa esta operación, un puntero a una matriz de identificadores de interfaz.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_OUTOFMEMORY.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)