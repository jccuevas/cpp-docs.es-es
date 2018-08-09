---
title: FactoryCache (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a09128bd334fc6e0987e39eaf51c19aadce34ea
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647552"
---
# <a name="factorycache-structure"></a>FactoryCache (estructura)
Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Comentarios  
 Contiene la ubicación de un generador de clases y un valor que identifica un registrados wrt o el objeto COM de la clase.  
  
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