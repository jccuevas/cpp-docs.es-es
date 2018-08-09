---
title: DontUseNewUseMake (clase) | Microsoft Docs
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
ms.openlocfilehash: 32418b163cb31f5eaf20c9d2b3ff3a4b585850dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644104"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Comentarios  
 Impide el uso de operador **nueva** en `RuntimeClass`. Por lo tanto, debe usar el [función](../windows/make-function.md) en su lugar.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new (operador)](../windows/dontusenewusemake-operator-new-operator.md)|Las sobrecargas de operador **nueva** e impide que se usa en `RuntimeClass`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Wrl Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make (función)](../windows/make-function.md)