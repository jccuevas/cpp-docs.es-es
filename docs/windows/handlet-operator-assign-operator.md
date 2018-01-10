---
title: 'Handlet:: operator = (operador) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68afd6b2a0a1c17cd032d6cea84aefde8c368204
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="handletoperator-operator"></a>HandleT::operator= (Operador)
Mueve el valor del objeto HandleT especificado al objeto HandleT actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Una referencia a valor r a un identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto HandleT actual.  
  
## <a name="remarks"></a>Comentarios  
 Esta operación invalida el objeto HandleT especificado por el parámetro `h`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)