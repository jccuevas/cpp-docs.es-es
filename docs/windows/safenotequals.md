---
title: SafeNotEquals | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeNotEquals
dev_langs: C++
helpviewer_keywords: SafeNotEquals function
ms.assetid: 032e45a8-4159-4b55-b7cc-ecd27f4e4788
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: dc77d2a8d4558fad3f1339edbfd7d9d8e1b102ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="safenotequals"></a>SafeNotEquals
Determina si dos números no son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeNotEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `t`  
 Primer número que se va a comparar. Debe ser de tipo T.  
  
 [in] `u`  
 Segundo número que se va a comparar. Debe ser de tipo U.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si `t` y `u` no son iguales; en caso contrario `false`.  
  
## <a name="remarks"></a>Comentarios  
 El método mejora `!=` porque `SafeNotEquals` permite comparar dos tipos diferentes de números.  
  
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
 [SafeEquals](../windows/safeequals.md)