---
title: SafeIntException::SafeIntException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef3c1d11c0f814699ca1492f7ec1fb49c43c3d76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892181"
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