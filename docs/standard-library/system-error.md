---
title: "&lt;system_error&gt; | Microsoft Docs"
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
  - "std.<system_error>"
  - "std::<system_error>"
  - "<system_error>"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error (encabezado)"
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;system_error&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado `<system_error>` para definir la clase de excepción `system_error` y plantillas relacionadas para procesar errores del sistema de bajo nivel.  
  
## Sintaxis  
  
```  
#include <system_error>  
```  
  
### Objetos  
  
|||  
|-|-|  
|[generic\_category](../Topic/generic_category.md)|Representa la categoría de errores genéricos.|  
|[system\_category](../Topic/system_category.md)|Representa la categoría de los errores producidos por los desbordamientos de bajo nivel del sistema.|  
  
### Typedefs  
  
|||  
|-|-|  
|[generic\_errno](../Topic/generic_errno.md)|Un tipo que representa la enumeración que proporciona los nombres simbólicos de todas las macros del código de error definido por POSIX en `<errno.h>`.|  
  
### Funciones  
  
|||  
|-|-|  
|[make\_error\_code](../Topic/make_error_code.md)|Crea un objeto `error_code`.|  
|[make\_error\_condition](../Topic/make_error_condition.md)|Crea un objeto `error_condition`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/operator==%20\(%3Csystem_error%3E\).md)|Comprueba si el objeto en el lado izquierdo del operador es igual al objeto en el lado derecho.|  
|[operator\!\=](../Topic/operator!=%20\(%3Csystem_error%3E\).md)|Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto en el lado derecho.|  
|[':?'.\<](../Topic/operator%3C%20\(%3Csystem_error%3E\).md)|Prueba si un objeto es menor que el objeto pasado para la comparación.|  
  
### Enumeraciones  
  
|||  
|-|-|  
|[errc](../Topic/errc%20Enumeration.md)|Proporciona nombres simbólicos para todas las macros de código de error definidas por Posix en `<errno.h>`.|  
  
### Clases y Structs  
  
|||  
|-|-|  
|[error\_category](../standard-library/error-category-class.md)|Representa el resumen, la base de común para los objetos que describe una categoría de códigos de error.|  
|[error\_code](../standard-library/error-code-class.md)|Representa los errores del sistema de bajo nivel que son implementación\- concretos.|  
|[error\_condition](../standard-library/error-condition-class.md)|Representa los códigos de error definidos por el usuario.|  
|[is\_error\_code\_enum](../standard-library/is-error-code-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración de [error\_code \(Clase\)](../standard-library/error-code-class.md) .|  
|[is\_error\_condition\_enum](../standard-library/is-error-condition-enum-class.md)|Representa un predicado de tipo que comprueba la enumeración de [error\_condition \(Clase\)](../standard-library/error-condition-class.md) .|  
|[system\_error](../standard-library/system-error-class.md)|Representa la clase base para todas las excepciones que se producen para designar un desbordamiento de bajo nivel del sistema.|  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)