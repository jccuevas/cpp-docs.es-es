---
title: "&lt;new&gt; | Microsoft Docs"
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
  - "std::<new>"
  - "<new>"
  - "std.<new>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new (encabezado)"
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;new&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varios tipos y funciones que controlan la asignación y liberación de almacenamiento bajo el control del programa.  También define los componentes para la creación de informes de errores de administración de almacenamiento.  
  
## Sintaxis  
  
```  
  
#include <new>  
  
```  
  
## Comentarios  
 Algunas de las funciones declaradas en este encabezado son reemplazables.  La implementación proporciona una versión predeterminada, cuyo comportamiento se describe en este documento.  No obstante, un programa puede definir una función con la misma firma para reemplazar la versión predeterminada en tiempo de vinculación.  La versión de reemplazo debe cumplir los requisitos descritos en este documento.  
  
### Objetos  
  
|||  
|-|-|  
|[nothrow](../Topic/nothrow%20\(%3Cnew%3E\).md)|Proporciona un objeto que se usará como argumento las versiones `nothrow` de **new** y **delete**.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[new\_handler](../Topic/new_handler.md)|Tipo que apunta a una función que se puede usar como un nuevo controlador.|  
  
### Funciones  
  
|||  
|-|-|  
|[set\_new\_handler](../Topic/set_new_handler.md)|Instala una función de usuario que se llama cuando el nuevo controlador no puede asignar memoria.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para objetos individuales.|  
|[operator delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para una matriz de objetos.|  
|[operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md)|Función a la que llama una expresión new para asignar el almacenamiento para objetos individuales.|  
|[operator new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md)|Función a la que llama una expresión new para asignar el almacenamiento para una matriz de objetos.|  
  
### Clases  
  
|||  
|-|-|  
|[bad\_alloc \(Clase\)](../standard-library/bad-alloc-class.md)|Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.|  
|[nothrow\_t \(Clase\)](../standard-library/nothrow-t-structure.md)|Clase que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)