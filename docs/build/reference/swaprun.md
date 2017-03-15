---
title: "/SWAPRUN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/swaprun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN (opción de editbin)"
  - "SWAPRUN (opción de editbin)"
  - "-SWAPRUN (opción de editbin)"
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /SWAPRUN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## Comentarios  
 Esta opción edita la imagen para indicar al sistema operativo que debe copiar la imagen a un archivo de intercambio y ejecutarla desde dicho archivo.  Utilice esta opción para imágenes que residan en redes o en medios extraíbles.  
  
 Puede agregar o quitar los calificadores NET y CD:  
  
-   NET indica que la imagen reside en una red.  
  
-   CD indica que la imagen reside en un CD\-ROM o en un medio extraíble similar.  
  
-   Utilice \!NET y \!CD para deshacer los efectos de NET y CD.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)