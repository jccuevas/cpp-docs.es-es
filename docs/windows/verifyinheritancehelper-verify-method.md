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
ms.openlocfilehash: 8a337dcce390f8dc3b634018af602bc3e62e719b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396095"
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

[VerifyInheritanceHelper (estructura)](../windows/verifyinheritancehelper-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)