---
title: "Chaininterfaces:: Verify (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs: C++
helpviewer_keywords: Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d34d117091fd8807dfefda074e510910bf059560
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify (Método)
Comprueba que cada interfaz definido por los parámetros de plantilla `I0` a través de `I9` hereda de IUnknown o IInspectable y que `I0` hereda de `I1` a través de `I9`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se produce un error en la operación de comprobación, un `static_assert` emite un mensaje de error que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Parámetros de plantilla `I0` y `I1` son necesarios y los parámetros `I2` a través de `I9` son opcionales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)