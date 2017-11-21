---
title: 'Weakref:: operator&amp; operador | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::operator&
dev_langs: C++
helpviewer_keywords: operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c13e025b0a15998a6420b29b0bb23ff65824f14e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="weakrefoperatoramp-operator"></a>Weakref:: operator&amp; (operador)
Devuelve un objeto ComPtrRef que representa al objeto WeakRef actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto ComPtrRef que representa el objeto WeakRef actual.  
  
## <a name="remarks"></a>Comentarios  
 Se trata de un operador auxiliar interno que no está diseñado para utilizarse en el código.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)