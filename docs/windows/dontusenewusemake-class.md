---
title: DontUseNewUseMake (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f343d0b47d50cd375d186c29ff55b91898aa9c61
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872333"
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