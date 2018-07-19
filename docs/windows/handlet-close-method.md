---
title: 'Handlet:: Close (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 4f0c1e47420106651cfe0526d6d212e9819a72ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873256"
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