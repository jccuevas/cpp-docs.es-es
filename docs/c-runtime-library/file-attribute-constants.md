---
title: "Constantes de atributo de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A_HIDDEN"
  - "_A_NORMAL"
  - "_A_SUBDIR"
  - "_A_RDONLY"
  - "A_NORMAL"
  - "A_SUBDIR"
  - "_A_SYSTEM"
  - "c.constants.file"
  - "_A_HIDDEN"
  - "A_RDONLY"
  - "_A_ARCH"
  - "A_ARCH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_A_ARCH (constante)"
  - "_A_HIDDEN (constante)"
  - "_A_NORMAL (constante)"
  - "_A_RDONLY (constante)"
  - "_A_SUBDIR (constante)"
  - "_A_SYSTEM (constante)"
  - "constantes [C++], atributos de archivo"
  - "constantes de atributo de archivo [C++]"
  - "archivos [C++], constantes de atributo de archivo"
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Constantes de atributo de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <io.h>  
```  
  
## Comentarios  
 Estas constantes especifican los atributos actuales del archivo o el directorio especificado por la función.  
  
 Los atributos se representan mediante las constantes de manifiesto siguientes:  
  
 `_A_ARCH`  
 Archivo.  Conjunto siempre que esté cambiado, y borrado por el comando AUXILIAR.  Value: 0x20  
  
 `_A_HIDDEN`  
 Archivo oculto.  Visto no normalmente al comando de DIR, a menos que se utilice la opción \/AH.  Devuelve información sobre los archivos normales junto con los archivos con este atributo.  Value: 0x02  
  
 `_A_NORMAL`  
 Normal.  El archivo se puede leer o escribir sin en la restricción.  Value: 0x00  
  
 `_A_RDONLY`  
 Sólo lectura.  El archivo no se puede abrir para escribir, y un archivo con el mismo nombre no se puede crear.  Value: 0x01  
  
 `_A_SUBDIR`  
 Subdirectorio.  Value: 0x10  
  
 `_A_SYSTEM`  
 Archivo de sistema.  Visto no normalmente al comando de DIR, a menos que se utilice la opción \/AS.  Value: 0x04  
  
 Las varias constantes pueden combinarse con OR el operador \(&#124;\).  
  
## Vea también  
 [Funciones de búsqueda de nombre de archivo](../c-runtime-library/filename-search-functions.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)