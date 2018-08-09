---
title: Miembro de datos ActivationID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b9fd147f0821e14e825b2a8c0e8d7ad35104fe9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653019"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId (Miembro de datos)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLSID*  
 Id. de interfaz.  
  
 *getRuntimeName*  
 Una función que recupera el nombre de Windows en tiempo de ejecución de un objeto.  
  
## <a name="remarks"></a>Comentarios  
 Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de Windows en tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [CreatorMap (estructura)](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)