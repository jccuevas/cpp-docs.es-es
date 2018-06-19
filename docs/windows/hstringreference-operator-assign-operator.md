---
title: 'Hstringreference:: operator = (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73ec71526d340aafb16ddf2af274dce7ad0e9cbd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875544"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= (Operador)
Mueve el valor de otro objeto de HStringReference al objeto HStringReference actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### <a name="parameters"></a>Parámetros  
 `other`  
 Un objeto HStringReference existente.  
  
## <a name="remarks"></a>Comentarios  
 El valor de la existente `other` objeto se copia en el objeto de HStringReference actual y, a continuación, el `other` se destruye el objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)