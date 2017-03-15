---
title: bad_exception (Clase)| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.bad_exception
- bad_exception
- std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7870c00b019718188b80a64e0102638deb76f588
ms.lasthandoff: 02/24/2017

---
# <a name="badexception-class"></a>Clase bad_exception
La clase describe una excepción que se puede iniciar desde un controlador inesperado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>Comentarios  
 [unexpected](../standard-library/exception-functions.md#unexpected) inicia `bad_exception` en lugar de terminar o de llamar a otra función especificada con [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` está incluido en la lista de excepciones de una función.  
  
 El valor que devuelve **what** es una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.  
  
 Para obtener una lista de miembros heredados por la clase `bad_exception`, vea [Exception (Clase)](../standard-library/exception-class.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de [unexpected](../standard-library/exception-functions.md#unexpected) iniciando `bad_exception`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<exception>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[Exception (Clase)](../standard-library/exception-class.md)
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


