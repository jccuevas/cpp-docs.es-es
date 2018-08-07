---
title: Método Handlet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69f3f2c756d158954676f6fc42941b1b80f4345e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569923"
---
# <a name="handletclose-method"></a>HandleT::Close (Método)
Cierra el actual **HandleT** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Comentarios  
 El identificador que subyace a actual **HandleT** está cerrado y el **HandleT** está establecido en el estado no válido.  
  
 Si el identificador no se cierra correctamente, se produce una excepción en el subproceso de llamada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)