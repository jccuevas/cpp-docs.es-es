---
title: "Constantes de permiso de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_S_IWRITE"
  - "_S_IREAD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_S_IREAD (función)"
  - "_S_IWRITE (función)"
  - "constantes [C++], atributos de archivo"
  - "permisos de archivo [C++]"
  - "S_IREAD (constante)"
  - "S_IWRITE (constante)"
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Constantes de permiso de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## Comentarios  
 Una de estas constantes se requiere cuando se especifica `_O_CREAT` \(`_open`, `_sopen`\).  
  
 El argumento de `pmode` especifica las configuraciones de permisos del archivo como sigue.  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_S_IREAD`|Lectura permitida|  
|`_S_IWRITE`|Escribir permitida|  
|`_S_IREAD`  &#124; `_S_IWRITE`|Lectura y escritura permitidas|  
  
 Cuando se utiliza como argumento de `pmode` para `_umask`, la constante de manifiesto establece la configuración de permisos, como sigue.  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_S_IREAD`|Escritura no permitida \(el archivo es de sólo lectura\)|  
|`_S_IWRITE`|La lectura no permitido \(el archivo es de sólo escritura\)|  
|`_S_IREAD`  &#124; `_S_IWRITE`|Ni leer ni escribir permitida|  
  
## Vea también  
 [\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../c-runtime-library/reference/umask.md)   
 [Tipos estándar](../c-runtime-library/standard-types.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)