---
title: Método Interfacetraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 46edd67f-7952-4552-a157-55e823f616c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 404c5fc8680089aeac49b0cda655e9cbd0d4ecd9
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603053"
---
# <a name="interfacetraitsverify-method"></a>InterfaceTraits::Verify (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Comentarios  
 Comprueba que `Base` se deriva correctamente.  
  
 Para obtener más información acerca de `Base`, vea la sección de definiciones de tipo público en [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)