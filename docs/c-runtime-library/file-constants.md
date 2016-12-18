---
title: "Constantes de archivo | Microsoft Docs"
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
  - "_O_EXCL"
  - "_O_RDWR"
  - "_O_APPEND"
  - "_O_RDONLY"
  - "_O_TRUNC"
  - "_O_CREAT"
  - "_O_WRONLY"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_O_APPEND (constante)"
  - "_O_CREAT (constante)"
  - "_O_EXCL (constante)"
  - "_O_RDONLY (constante)"
  - "_O_RDWR (constante)"
  - "_O_TRUNC (constante)"
  - "_O_WRONLY (constante)"
  - "O_APPEND (constante)"
  - "O_CREAT (constante)"
  - "O_EXCL (constante)"
  - "O_RDONLY (constante)"
  - "O_RDWR (constante)"
  - "O_TRUNC (constante)"
  - "O_WRONLY (constante)"
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <fcntl.h>  
  
```  
  
## Comentarios  
 La expresión de entero formada de uno o más de estas constantes determina el tipo de operaciones de lectura o escritura permitidas.  Se calculan combinando una o más constantes con una constante de modalidad de traducción.  
  
 Las constantes de archivo son los siguientes:  
  
 `_O_APPEND`  
 Coloca el puntero de archivo en el final del archivo antes de cada operación de escritura.  
  
 `_O_CREAT`  
 Crea y abre un nuevo archivo para escribir; esto no tiene ningún efecto si existe el archivo especificado por el *nombre de archivo* .  
  
 `_O_EXCL`  
 Devuelve un valor de error si existe el archivo especificado por el *nombre de archivo* .  Solo se aplica cuando se utiliza con `_O_CREAT`.  
  
 `_O_RDONLY`  
 Archivo de Abrir para leer solo; si se especifica este marcador, ni `_O_RDWR` ni `_O_WRONLY` puede asignar.  
  
 `_O_RDWR`  
 Archivo de Abrir para la lectura y escritura; si se especifica este marcador, ni `_O_RDONLY` ni `_O_WRONLY` puede asignar.  
  
 `_O_TRUNC`  
 Los Abrir y truncan un archivo existente a la longitud cero; el archivo debe tener permisos de escritura.  El contenido del archivo se destruyen.  Si se especifica este marcador, no puede especificar `_O_RDONLY`.  
  
 `_O_WRONLY`  
 Archivo de Abrir para escribir sólo; si se especifica este marcador, ni `_O_RDONLY` ni `_O_RDWR` puede asignar.  
  
## Vea también  
 [\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)