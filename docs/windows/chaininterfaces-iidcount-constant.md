---
title: Chaininterfaces constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417ca38ab44d334fd26c503edc2727934983c39d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648147"
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount (Constante)
El número total de identificadores contenidos en las interfaces especificadas por los parámetros de plantilla de interfaz *I0* a través de *I9*.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El número total de identificadores de interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Parámetros de plantilla *I0* y *I1* son necesarios y los parámetros *I2* a través de *I9* son opcionales. El recuento IID de cada interfaz suele ser 1.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)