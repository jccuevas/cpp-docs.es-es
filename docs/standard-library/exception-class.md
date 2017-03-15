---
title: exception (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.exception
- exception
- std::exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 6983a0e24f7422b708d7fbbfca6689bec629cb06
ms.lasthandoff: 02/24/2017

---
# <a name="exception-class"></a>Clase exception
La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C++.  
  
## <a name="syntax"></a>Sintaxis  
```  
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };  
``` 
## <a name="remarks"></a>Comentarios  
 En concreto, esta clase base es la raíz de las clases de excepción estándar definidas en [\<stdexcept>](../standard-library/stdexcept.md). El constructor predeterminado no especifica el valor de cadena de C devuelto por `what`, pero lo pueden definir los constructores de ciertas clases derivadas como una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.  
  
 El parámetro `int` le permite especificar que no se debe asignar ninguna memoria. El valor de `int` se omite.  
  
> [!NOTE]
>  Los constructores `exception(const char* const &message)` y `exception(const char* const &message, int)` son extensiones de Microsoft para la biblioteca estándar de C++.  
  
## <a name="example"></a>Ejemplo  
 Para obtener ejemplos del uso de las clases de excepción estándar que heredan de la clase `exception`, vea cualquiera de las clases definidas en [\<stdexcept>](../standard-library/stdexcept.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<exception>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




