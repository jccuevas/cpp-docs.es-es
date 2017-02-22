---
title: "Compatibilidad con versiones anteriores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad con versiones anteriores"
  - "compatibilidad con versiones anteriores, bibliotecas en tiempo de ejecución de C"
  - "compatibilidad, bibliotecas en tiempo de ejecución de C"
  - "CRT, compatibilidad"
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Compatibilidad con versiones anteriores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para la compatibilidad entre versiones del producto, la biblioteca OLDNAMES.LIB asigna antiguos nombres nuevos nombres.  Por ejemplo, mapas de `open` a `_open`.  Debe vinculación explícita con OLDNAMES.LIB cuando se compila con combinaciones siguientes de opciones de la línea de comandos:  
  
-   `/Zl` \(omitir el nombre de la biblioteca predeterminada del archivo objeto\) y `/Ze` \(el valor predeterminado — utilizar las extensiones de Microsoft\)  
  
-   `/link` \(vinculador\- CONTROL\), `/NOD` \(ninguna búsqueda de configuración por defecto\- biblioteca\), y `/Ze`  
  
 Para obtener más información sobre las opciones de la línea de comandos del compilador, vea [Referencia del compilador](../build/reference/compiler-options.md).  
  
## Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)