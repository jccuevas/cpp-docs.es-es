---
title: "Archivos de resultados de LIB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de salida, LIB"
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos de resultados de LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos de salida producidos por LIB dependerán del modo en que se esté utilizando, como se indica en la tabla siguiente.  
  
|Modo|Resultados|  
|----------|----------------|  
|Predeterminado \(compilar o modificar una biblioteca\)|Biblioteca COFF \(.lib\)|  
|Extraer un miembro con la opción \/EXTRACT|Archivo objeto \(.obj\)|  
|Compilar un archivo de exportación y una biblioteca de importación con la opción \/DEF|Biblioteca de importación \(.lib\) y archivo de exportación \(.exp\)|  
  
## Vea también  
 [Información general sobre LIB](../../build/reference/overview-of-lib.md)