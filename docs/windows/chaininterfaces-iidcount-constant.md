---
title: Chaininterfaces (constante) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs: C++
helpviewer_keywords: IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a1336bb5b8b43e833325c304a4d870220a40b84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount (Constante)
El número total de identificadores contenidos en las interfaces especificadas por los parámetros de plantilla interfaz `I0` a través de `I9`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El número total de identificadores de interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Parámetros de plantilla `I0` y `I1` son necesarios y los parámetros `I2` a través de `I9` son opcionales. El recuento IID de cada interfaz suele ser 1.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)