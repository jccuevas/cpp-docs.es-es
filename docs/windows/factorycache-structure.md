---
title: FactoryCache (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0fc48c9a3651e8c5a6609886862c2f73c5707638
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="factorycache-structure"></a>FactoryCache (estructura)
Admite la infraestructura de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Comentarios  
 Contiene la ubicación de un generador de clases y un valor que identifica un registrados wrt u objeto de clase de COM.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FactoryCache::cookie (miembro de datos)](../windows/factorycache-cookie-data-member.md)|Contiene un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado y se utiliza posteriormente para anular el registro del objeto.|  
|[FactoryCache::factory (miembro de datos)](../windows/factorycache-factory-data-member.md)|Apunta a un generador de clases COM o en tiempo de ejecución de Windows.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `FactoryCache`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)