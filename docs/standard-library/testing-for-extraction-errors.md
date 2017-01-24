---
title: "Comprobar errores de extracci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "errores de extracción"
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comprobar errores de extracci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genere las funciones de procesamiento del error, descritas en [Funciones de procesamiento del error](../standard-library/output-file-stream-member-functions.md), aplique los flujos de entrada.  Pruebas de los errores durante la recuperación es importante.  Considere esta instrucción:  
  
```  
cin >> n;  
```  
  
 Si `n` es un entero, un valor mayor que 32.767 \(el máximo permitido valor, o MAX\_INT\) establece el bit de `fail` de secuencia, y el objeto de `cin` deja de estar inutilizables.  Todas las extracciones subsiguientes generan un retorno inmediato sin el valor almacenado.  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)