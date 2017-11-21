---
title: 'Hstringreference:: operator&lt; operador | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs: C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46d839cd10144877ee4af561ce9e1ab52343de83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: operator&lt; (operador)
Indica si el primer parámetro es menor que el segundo parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs`puede ser una referencia a un HStringReference.  
  
 `rhs`  
 El segundo parámetro para comparar.  `rhs`puede ser una referencia a un HStringReference.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si el `lhs` parámetro es menor que el `rhs` parámetro; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)