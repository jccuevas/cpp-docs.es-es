---
title: Issame constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9d1ae2b4ea4ad4769a770d503ff8bd82c91a53a
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608792"
---
# <a name="issamevalue-constant"></a>IsSame::value (Constante)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  template <typename T1, typename T2>  
struct IsSame  
{  
    static const bool value = false;  
};  
  
template <typename T1>  
struct IsSame<T1, T1>  
{  
    static const bool value = true;  
};  
```  
  
## <a name="remarks"></a>Comentarios  
 Indica si un tipo es igual a otro.  
  
 `value` es **true** si los parámetros de plantilla son los mismos, y **false** si los parámetros de plantilla son diferentes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [IsSame (estructura)](../windows/issame-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)