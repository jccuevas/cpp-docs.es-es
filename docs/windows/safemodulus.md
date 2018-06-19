---
title: SafeModulus | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 653293ac04be1e3a04e90412a9d9d8b988773329
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888873"
---
# <a name="safemodulus"></a>SafeModulus
Realiza la operación de módulo en dos números.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `t`  
 Divisor. Debe ser de tipo T.  
  
 [in] `u`  
 Dividendo. Debe ser de tipo U.  
  
 [out] `result`  
 El parámetro donde `SafeModulus` almacena el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si se produce ningún error; `false` si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de módulo único sin necesidad de crear una instancia de la [SafeInt (clase)](../windows/safeint-class.md).  
  
> [!NOTE]
>  Este método solo debe usarse cuando se debe proteger una sola operación matemática. Si hay varias operaciones, debe usar la `SafeInt` clase en lugar de llamar a las funciones individuales independientes.  
  
 Para obtener más información acerca de los tipos de plantilla T y U, consulte [SafeInt (funciones)](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Vea también  
 [SafeInt (funciones)](../windows/safeint-functions.md)   
 [Biblioteca SafeInt](../windows/safeint-library.md)   
 [SafeInt (clase)](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)