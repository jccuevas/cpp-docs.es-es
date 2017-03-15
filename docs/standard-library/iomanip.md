---
title: "&lt; iomanip &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iomanip/std::<iomanip>"
  - "std::<iomanip>"
  - "<iomanip>"
  - "std.<iomanip>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iomanip (encabezado)"
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt; iomanip &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar `iostreams``<iomanip>` para definir varios manipuladores que toman cada uno de ellos un solo argumento.  
  
## Sintaxis  
  
```  
  
#include <iomanip>  
  
```  
  
## Comentarios  
 Cada uno de estos manipuladores devuelve un tipo sin especificar, denominado de **T1** a **T10**, que sobrecarga `basic_istream`\<**Elem**, **Tr**\>`::`[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md) y `basic_ostream`\<**Elem**, **Tr**\>`::`[operator\<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md).  
  
### Manipuladores  
  
|||  
|-|-|  
|[get\_money](../Topic/%3Ciomanip%3E%20get_money.md)|Obtiene un importe monetario, opcionalmente en formato internacional.|  
|[get\_time](../Topic/%3Ciomanip%3E%20get_time.md)|Obtiene una hora en una estructura de hora con un formato especificado.|  
|[put\_money](../Topic/%3Ciomanip%3E%20put_money.md)|Proporciona un importe monetario, opcionalmente en formato internacional.|  
|[put\_time](../Topic/%3Ciomanip%3E%20put_time.md)|Proporciona una hora en una estructura de hora y una cadena de formato que se va a usar.|  
|[entrecomillado](../Topic/quoted.md)|Permite realizar un práctico recorrido de ida y vuelta de cadenas con operadores de inserción y extracción.|  
|[resetiosflags](../Topic/resetiosflags.md)|Borra las marcas especificadas.|  
|[setbase](../Topic/setbase.md)|Establece la base de los enteros.|  
|[setfill](../Topic/setfill.md)|Establece el carácter que se usará para rellenar los espacios en una presentación justificada a la derecha.|  
|[setiosflags](../Topic/setiosflags.md)|Establece las marcas especificadas.|  
|[setprecision](../Topic/setprecision.md)|Establece la precisión de los valores de punto flotante.|  
|[setw](../Topic/setw.md)|Especifica el ancho del campo de presentación.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)