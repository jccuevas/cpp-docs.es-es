---
title: "Constantes del campo st_mode de la estructura _stat | Microsoft Docs"
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
  - "S_IFCHR"
  - "S_IFDIR"
  - "_S_IWRITE"
  - "S_IFMT"
  - "_S_IFDIR"
  - "_S_IREAD"
  - "S_IEXEC"
  - "_S_IEXEC"
  - "_S_IFMT"
  - "S_IWRITE"
  - "S_IFREG"
  - "S_IREAD"
  - "_S_IFCHR"
  - "_S_IFREG"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_S_IEXEC (constante)"
  - "_S_IFCHR (constante)"
  - "_S_IFDIR (constante)"
  - "_S_IFMT (constante)"
  - "_S_IFREG (constante)"
  - "_S_IREAD (función)"
  - "_S_IWRITE (función)"
  - "S_IEXEC (constante)"
  - "S_IFCHR (constante)"
  - "S_IFDIR (constante)"
  - "S_IFMT (constante)"
  - "S_IFREG (constante)"
  - "S_IREAD (constante)"
  - "S_IWRITE (constante)"
  - "st_mode (constantes de campo)"
  - "stat (estructura)"
  - "stat (estructura), constantes"
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes del campo st_mode de la estructura _stat
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## Comentarios  
 Estas constantes se utilizan para indicar el tipo de archivo en el campo de **st\_mode** de [estructura de \_stat](../c-runtime-library/standard-types.md).  
  
 Las constantes de la máscara de bits se describen a continuación:  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_S_IFMT`|Máscara de tipo de archivo|  
|`_S_IFDIR`|Directorio|  
|`_S_IFCHR`|Especial de caracteres \(indica un dispositivo si conjunto\)|  
|`_S_IFREG`|Estándar|  
|`_S_IREAD`|Permiso de Lectura, propietario|  
|`_S_IWRITE`|Permiso de escritura, propietario|  
|`_S_IEXEC`|Execute y permiso de búsqueda, propietario|  
  
## Vea también  
 [\_stat, \_wstat \(Funciones\)](../c-runtime-library/reference/stat-functions.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [Tipos estándar](../c-runtime-library/standard-types.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)