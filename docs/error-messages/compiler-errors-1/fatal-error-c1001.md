---
title: "Error irrecuperable C1001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1001"
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ERROR INTERNO DEL COMPILADOR \(archivo del compilador archivo, línea número\)  
  
 El compilador no consigue generar código correcto para una construcción, probablemente por la combinación de una expresión y una opción de optimización.  Intente quitar una o varias opciones de optimización y vuelva a compilar la función que contiene la línea indicada en el mensaje de error.  
  
 Probablemente se solucione el problema quitando una o más opciones de optimización.  Para determinar qué opción produce el error, quite las opciones una a una y vuelva a compilar hasta que el mensaje de error desaparezca.  Las opciones que suelen producir este tipo de error son: **\/Og**, **\/Oi** y `/Oa`.  Una vez determinada la opción causante del error, podrá deshabilitarla mediante pragma [optimize](../../preprocessor/optimize.md) en torno a la función donde se produce el error y continuar utilizando la opción en el resto del módulo.  
  
 Microsoft Knowledge Base tiene más información sobre C1001; vea [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 Pruebe a escribir de nuevo la línea donde se notifica el error o varias de las líneas anteriores y posteriores.