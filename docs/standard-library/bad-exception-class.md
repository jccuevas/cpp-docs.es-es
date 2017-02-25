---
title: "Clase bad_exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.bad_exception"
  - "bad_exception"
  - "std::bad_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_exception (clase)"
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# Clase bad_exception
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase describe una excepción que se puede iniciar desde un controlador inesperado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>Comentarios  
 [inesperado](../Topic/%3Cexception%3E%20functions.md#unexpected) producirá un `bad_exception` en lugar de terminación o en lugar de llamar a otra función que se especifica con [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) Si `bad_exception` se incluye en la lista de excepciones de una función.  
  
 El valor devuelto por **qué** es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.  
  
 Para obtener una lista de miembros heredados por el `bad_exception` de clases, consulte [clase exception](../standard-library/exception-class1.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) para obtener un ejemplo del uso de [inesperado](../Topic/%3Cexception%3E%20functions.md#unexpected) generando un `bad_exception`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< (excepción)>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[Clase Exception](../standard-library/exception-class1.md)
 [seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

