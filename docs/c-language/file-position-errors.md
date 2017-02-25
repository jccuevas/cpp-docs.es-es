---
title: "Errores de posici&#243;n de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "punteros a archivos [C++], errores de posición de archivo"
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Errores de posici&#243;n de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.9.9.1, 4.9.9.4** Valor en el que establecen la macro `errno` las funciones `fgetpos` o `ftell` cuando se produce un error  
  
 Cuando `fgetpos` o `ftell` producen un error, `errno` es establece en la constante de manifiesto `EINVAL` si la posición no es válida o EBADF si el número de archivo es incorrecto.  Las constantes se definen en ERRNO.H.  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)