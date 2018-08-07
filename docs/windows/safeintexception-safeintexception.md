---
title: SafeIntException::SafeIntException | Microsoft Docs
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
ms.openlocfilehash: 744bf034572745cd88a35f47a1ca2da03e900fd8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606662"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Crea un **SafeIntException** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *código*  
 Un valor de datos enumerado que describe el error que se ha producido.  
  
## <a name="remarks"></a>Comentarios  
 Los valores posibles de *código* se definen en el archivo Safeint.h. Para mayor comodidad, también se muestran aquí los valores posibles.  
  
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