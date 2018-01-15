---
title: "Verifyinheritancehelper:: Verify (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs: C++
helpviewer_keywords: Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffc08fd7cd59d463d5a53ababf3acb6baef9e3ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static void Verify();  
```  
  
## <a name="remarks"></a>Comentarios  
 Comprueba las dos interfaces especificadas por los parámetros de plantilla actual y determina si una interfaz se deriva de la otra.  
  
 Se genera un error si una interfaz no se deriva de la otra.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [VerifyInheritanceHelper (estructura)](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)