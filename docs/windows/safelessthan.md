---
title: SafeLessThan | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c490f02f6c27d517095ab3f75a31bb03fe14f63
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="safelessthan"></a>SafeLessThan
Determina si un número es menor que otro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeLessThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `t`  
 Primer número. Debe ser de tipo T.  
  
 [in] `u`  
 El segundo número. Debe ser de tipo U.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si `t` es menor que `u`; en caso contrario `false`.  
  
## <a name="remarks"></a>Comentarios  
 Este método mejora el operador de comparación estándar porque `SafeLessThan` permite comparar dos tipos diferentes de número.  
  
 Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de comparación único sin necesidad de crear una instancia de la [SafeInt (clase)](../windows/safeint-class.md).  
  
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
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)