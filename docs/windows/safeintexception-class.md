---
title: SafeIntException (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 961fc2f2050336469f5944f603c0db3c6291a176
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33895780"
---
# <a name="safeintexception-class"></a>SafeIntException (Clase)
El `SafeInt` clase utiliza `SafeIntException` para determinar por qué no se puede completar una operación matemática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class SafeIntException;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
 [SafeIntException::SafeIntException](../windows/safeintexception-safeintexception.md)  
 Crea un objeto `SafeIntException`.  
  
## <a name="remarks"></a>Comentarios  
 El [SafeInt (clase)](../windows/safeint-class.md) es la única clase que usa el `SafeIntException` clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [SafeIntException (clase)](../windows/safeintexception-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca SafeInt](../windows/safeint-library.md)   
 [SafeInt (clase)](../windows/safeint-class.md)