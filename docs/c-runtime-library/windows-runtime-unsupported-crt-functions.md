---
title: "Funciones de CRT no compatibles con Windows en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones CRT no admitidas, Windows en tiempo de ejecución"
  - "Windows en tiempo de ejecución, funciones CRT no admitidas"
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones de CRT no compatibles con Windows en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas API en tiempo de ejecución de C \(CRT\) no se pueden usar en aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] que se ejecutan en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  Estas aplicaciones se crean con la marca de compilador\/ZW.  Para más información sobre funciones CRT no admitidas, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
 Todas las API en CRT se describen en la sección [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md) de la documentación.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)