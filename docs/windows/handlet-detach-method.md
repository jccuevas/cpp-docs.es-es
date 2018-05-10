---
title: 'Handlet:: Detach (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="handletdetach-method"></a>HandleT::Detach (Método)
Desasocia el objeto de HandleT actual de su identificador subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El identificador subyacente.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se completa esta operación, el HandleT actual se establece en el estado no válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)