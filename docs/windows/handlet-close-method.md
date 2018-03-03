---
title: "Handlet:: Close (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2edd3fee9893c72685eb334bf4b361997646b7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="handletclose-method"></a>HandleT::Close (Método)
Cierra el actual objeto HandleT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Comentarios  
 El identificador que subyace en la HandleT actual se cierra y el HandleT se establece en el estado no válido.  
  
 Si el identificador no se cierra correctamente, se produce una excepción en el subproceso que realiza la llamada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)