---
title: 'Handlet:: operator = (operador) | Microsoft Docs'
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
ms.openlocfilehash: ab629946b9fc5acec6b0fb0ba8f573a3fa90a031
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570046"
---
# <a name="handletoperator-operator"></a>HandleT::operator= (Operador)
Mueve el valor del elemento especificado **HandleT** el objeto actual **HandleT** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Una referencia rvalue a un identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia a la actual **HandleT** objeto.  
  
## <a name="remarks"></a>Comentarios  
 Esta operación invalida la **HandleT** objeto especificado por el parámetro *h*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)