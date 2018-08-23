---
title: Internalclose (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc3f01227cb37285f11ef8256d0b101f156871b5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605521"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose (Método)

Cierra el actual **HandleT** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
virtual bool InternalClose();
```

## <a name="return-value"></a>Valor devuelto

**True** si actual **HandleT** cerrado correctamente; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

**InternalClose()** es **protegido**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)