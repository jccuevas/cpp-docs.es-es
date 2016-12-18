---
title: "exception (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.exception"
  - "exception"
  - "std::exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception (clase)"
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exception (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C\+\+.  
  
## Sintaxis  
  
```  
class exception {  
public:  
    exception();  
    exception(const char * const &message);  
    exception(const char * const &message, int);  
    exception(const exception &right);  
    exception& operator=(const exception &right);  
    virtual ~exception();  
    virtual const char *what() const;  
};  
```  
  
## Comentarios  
 Específicamente, esta clase base es la raíz de las clases de excepción estándar definidas en [\<stdexcept\>](../standard-library/stdexcept.md).  El valor de cadena de C devuelto por `what` queda sin especificar por el constructor predeterminado, pero se puede definir mediante las clases derivadas de constructores para ciertos como cadena implementación\- definido de C.  Ninguna de las funciones miembro producen cualquier excepción.  
  
 El parámetro de `int` permite especificar que la memoria esté asignada.  El valor de `int` se omite.  
  
> [!NOTE]
>  Los constructores `exception(const char * const &message)` y `exception(const char * const &message, int)` son extensiones de Microsoft de la biblioteca estándar de C\+\+.  
  
## Ejemplo  
 Para obtener ejemplos del uso de las clases de excepción estándar que heredan de la clase de `exception` , vea las cualquiera de las clases definidas en [\<stdexcept\>](../standard-library/stdexcept.md).  
  
## Requisitos  
 **Encabezado:** \<exception\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)