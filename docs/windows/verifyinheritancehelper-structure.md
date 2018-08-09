---
title: VerifyInheritanceHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a67e63748ee7650b2e99a6112f9725daf6cf13c6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652941"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (estructura)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *I*  
 Un tipo.  
  
 *base*  
 Otro tipo.  
  
## <a name="remarks"></a>Comentarios  
 Comprueba si una interfaz se deriva de otra interfaz.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify (método)](../windows/verifyinheritancehelper-verify-method.md)|Prueba de las dos interfaces especificadas por los parámetros de plantilla actual y determina si una interfaz se deriva de la otra.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)