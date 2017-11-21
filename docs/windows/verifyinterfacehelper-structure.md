---
title: VerifyInterfaceHelper (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::VerifyInterfaceHelper
dev_langs: C++
helpviewer_keywords: VerifyInterfaceHelper structure
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 51e18940786af52b86d17f2b54d6fe835c639904
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (estructura)
Admite la infraestructura de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   bool isWinRTInterface,  
   typename I  
>  
struct VerifyInterfaceHelper;  
  
template <  
   typename I  
>  
struct VerifyInterfaceHelper<false, I>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `I`  
 Una interfaz para comprobar.  
  
 `isWinRTInterface`  
  
## <a name="remarks"></a>Comentarios  
 Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[VerifyInterfaceHelper::Verify (método)](../windows/verifyinterfacehelper-verify-method.md)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `VerifyInterfaceHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)