---
title: Método Verifyinheritancehelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfcbb57694fc18944d199c1d4c74d8c74a335783
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599120"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
static void Verify();
```

## <a name="remarks"></a>Comentarios

Prueba de las dos interfaces especificadas por los parámetros de plantilla actual y determina si una interfaz se deriva de la otra.

Se genera un error si una interfaz no se derive de la otra.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[VerifyInheritanceHelper (estructura)](../windows/verifyinheritancehelper-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)