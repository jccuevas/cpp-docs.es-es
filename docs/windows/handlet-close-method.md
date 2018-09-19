---
title: Método Handlet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab919b3aeba45462a15900429493225f00909d5a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602459"
---
# <a name="handletclose-method"></a>HandleT::Close (Método)

Cierra el actual **HandleT** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

## <a name="remarks"></a>Comentarios

El identificador que subyace a actual **HandleT** está cerrado y el **HandleT** está establecido en el estado no válido.

Si el identificador no se cierra correctamente, se produce una excepción en el subproceso de llamada.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)