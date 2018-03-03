---
title: DontUseNewUseMake (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c09276fb761dcd1f2f5be78afa40606e262aa3e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Comentarios  
 Impide el uso de operador `new` en RuntimeClass. Por lo tanto, debe utilizar el [Make (función)](../windows/make-function.md) en su lugar.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new (operador)](../windows/dontusenewusemake-operator-new-operator.md)|Sobrecargas de operador `new` e impide que se usa en RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Namespace wrl](../windows/microsoft-wrl-details-namespace.md)   
 [Make (función)](../windows/make-function.md)