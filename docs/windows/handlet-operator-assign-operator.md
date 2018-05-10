---
title: 'Handlet:: operator = (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a13e8eb7e74625e185b59816b5794b0390e95e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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