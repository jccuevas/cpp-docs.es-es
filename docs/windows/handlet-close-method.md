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
ms.openlocfilehash: 7cbe76cdea5c8fadef818ede1d63d88e4437bdae
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651072"
---
# <a name="handletclose-method"></a>HandleT::Close (Método)
Cierra el actual **HandleT** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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