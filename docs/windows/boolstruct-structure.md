---
title: BoolStruct (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::BoolStruct
dev_langs: C++
helpviewer_keywords: BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7daa7527c8eea2cfca3b8933b9c3e1f042883e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>Comentarios  
 BoolStruct (estructura) define si una ComPtr administra la duración de los objetos de una interfaz. BoolStruct se usa internamente el [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operador.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[BoolStruct::Member (miembro de datos)](../windows/boolstruct-member-data-member.md)|Especifica que un [ComPtr](../windows/comptr-class.md) es o no lo está, administrar la duración de los objetos de una interfaz.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BoolStruct`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Namespace wrl](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType (operador)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)