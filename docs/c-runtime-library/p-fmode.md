---
title: "__p__fmode | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__p__fmode"
apilocation: 
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__fmode"
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __p__fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Señala la variable global de `_fmode` , que especifica el archivo predeterminado *de modalidad de traducción* para operaciones de E\/S de archivos.  
  
## Sintaxis  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## Valor devuelto  
 Puntero a la variable global de `_fmode` .  
  
## Comentarios  
 La función de `__p__fmode` es para uso interno, y no se debe llamar desde código de usuario.  
  
 El archivo de modalidad de traducción especifica `binary` o la traducción de `text` para [\_open](../c-runtime-library/reference/open-wopen.md) y operaciones de E\/S de [\_pipe](../c-runtime-library/reference/pipe.md) .  Para obtener más información, vea [\_fmode](../c-runtime-library/fmode.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_p\_\_fmode|stdlib.h|