---
title: "Orden de las opciones de CL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), establecer opciones"
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Orden de las opciones de CL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las opciones pueden encontrarse en cualquier parte de la línea de comandos de CL, excepto \/link, que debe situarse en último lugar.  El compilador comienza con las opciones especificadas en la [variable de entorno CL](../../build/reference/cl-environment-variables.md) y, después, lee la línea de comandos de izquierda a derecha, procesando los archivos de comandos en el orden en que los encuentra.  Cada opción se aplica a todos los archivos de la línea de comandos.  Si CL encuentra opciones en conflicto, utilizará la situada más a la derecha.  
  
## Vea también  
 [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)