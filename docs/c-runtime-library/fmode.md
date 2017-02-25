---
title: "_fmode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "fmode"
  - "_fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "traducción de archivo [C++], modo predeterminado"
  - "fmode (función)"
  - "_fmode (función)"
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La variable de `_fmode` establece el modo predeterminado del archivo \(el archivo traducción para el texto o la traducción del binario.  Esta variable global está desusado para las versiones funcionales más seguras [\_get\_fmode](../c-runtime-library/reference/get-fmode.md) y [\_set\_fmode](../c-runtime-library/reference/set-fmode.md), que se debe usar en lugar de la variable global.  Se declara en Stdlib.h como sigue.  
  
## Sintaxis  
  
```  
extern int _fmode;  
```  
  
## Comentarios  
 La configuración predeterminada de `_fmode` es `_O_TEXT` para la traducción de modo de texto.  `_O_BINARY` es el valor para el modo binario.  
  
 Puede cambiar el valor de `_fmode` de tres maneras:  
  
-   Vínculo con Binmode.obj.  Esto cambia la configuración inicial de `_fmode` a `_O_BINARY`, produciendo todos los archivos a menos que `stdin`, `stdout`, y `stderr` que se abrirá en modo binario.  
  
-   Haga una llamada a `_get_fmode` o a `_set_fmode` para obtener o establecer la variable global de `_fmode` , respectivamente.  
  
-   Cambie el valor de `_fmode` directamente estableciéndolo en el programa.  
  
## Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md)   
 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)