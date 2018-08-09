---
title: Miembro de datos Factorycache | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs:
- C++
helpviewer_keywords:
- cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3636cdb2c30d08547fd9085141aa9283bdc85c7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652388"
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie (Miembro de datos)
Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## <a name="remarks"></a>Comentarios  
 Contiene un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado y se utiliza posteriormente para anular el registro del objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [FactoryCache (estructura)](../windows/factorycache-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)