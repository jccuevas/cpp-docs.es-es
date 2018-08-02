---
title: Argtraits constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b6f0059d167b04c9a4b177d1851ad88133ef5cd3
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466561"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args (Constante)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Mantiene un recuento del número de parámetros el `Invoke` al método de interfaz de un delegado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando `args` es igual a -1 indica que no puede haber ninguna coincidencia para el `Invoke` firma del método.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ArgTraits (estructura)](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)