---
title: SafeIntException (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeIntException Class
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91f1c80273d0e1ed41ea86774c71fcbe8ad1bbf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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