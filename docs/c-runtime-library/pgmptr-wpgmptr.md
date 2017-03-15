---
title: "_pgmptr, _wpgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pgmptr"
  - "_pgmptr"
  - "wpgmptr"
  - "_wpgmptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_pgmptr (función)"
  - "_wpgmptr (función)"
  - "pgmptr (función)"
  - "wpgmptr (función)"
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _pgmptr, _wpgmptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ruta del archivo ejecutable.  Obsoleto; uso [\_get\_pgmptr](../c-runtime-library/reference/get-pgmptr.md) y [\_get\_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md).  
  
## Sintaxis  
  
```  
extern char *_pgmptr;  
extern wchar_t *_wpgmptr;  
```  
  
## Comentarios  
 Cuando un programa se ejecuta el intérprete de comandos \(Cmd.exe\), `_pgmptr` automáticamente se inicializa en la ruta de acceso completa del archivo ejecutable.  Por ejemplo, si Hello.exe está en C:\\BIN y C:\\BIN está en la ruta, `_pgmptr` se establece en C:\\BIN\\Hello.exe cuando se ejecuta:  
  
```  
C> hello   
```  
  
 Cuando un programa no se ejecuta desde la línea de comandos, `_pgmptr` haberse inicializado al nombre del programa \(el nombre base del archivo sin la extensión de nombre de archivo\) o un nombre de archivo, una ruta de acceso relativa, o una ruta de acceso completa.  
  
 `_wpgmptr` es el carácter ancho de `_pgmptr` con los programas que utilizan `wmain`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## Requisitos  
  
|Variable|Encabezado necesario|  
|--------------|--------------------------|  
|`_pgmptr`, `_wpgmptr`|\<stdlib.h\>|  
  
## Ejemplo  
 El programa siguiente muestra el uso de `_pgmptr`.  
  
```  
// crt_pgmptr.c  
// compile with: /W3  
// The following program demonstrates the use of _pgmptr.  
//  
#include <stdio.h>  
#include <stdlib.h>  
int main( void )  
{  
   printf("The full path of the executing program is : %Fs\n",   
     _pgmptr); // C4996  
   // Note: _pgmptr is deprecated; use _get_pgmptr instead  
}  
```  
  
 Puede utilizar `_wpgmptr` cambiando `%Fs` a `%S` y `main` a `wmain`.  
  
## Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)