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
ms.openlocfilehash: 351b38a002c470dcd3f53e8336e393f845fdb3cf
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569575"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Comentarios  
 Impide el uso de operador **nuevo** en RuntimeClass. Por lo tanto, debe usar el [función](../windows/make-function.md) en su lugar.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new (operador)](../windows/dontusenewusemake-operator-new-operator.md)|Las sobrecargas de operador **nuevo** e impide que se usa en RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Wrl Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make (función)](../windows/make-function.md)