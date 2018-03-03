---
title: SafeIntException::SafeIntException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85bf6bae5ba07154bdeb807171dd2d3df61d0774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Crea un objeto `SafeIntException`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `code`  
 Un valor de datos enumerado que describe el error que se ha producido.  
  
## <a name="remarks"></a>Comentarios  
 Los valores posibles de `code` se definen en el archivo Safeint.h. Para mayor comodidad, también se muestran aquí los valores posibles.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca SafeInt](../windows/safeint-library.md)   
 [SafeIntException (clase)](../windows/safeintexception-class.md)   
 [SafeInt (clase)](../windows/safeint-class.md)