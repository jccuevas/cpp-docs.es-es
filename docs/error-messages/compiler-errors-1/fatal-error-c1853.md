---
title: "Error irrecuperable C1853 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1853"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1853"
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error irrecuperable C1853
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El archivo de encabezado precompilado 'nombredearchivo' es de una versión anterior del compilador, o bien el encabezado precompilado es de C\+\+ y lo está utilizando desde C \(o viceversa\)  
  
 Causas posibles:  
  
-   El encabezado precompilado está compilado con una versión anterior del compilador.  En dicho caso, intente recompilar el encabezado con el compilador actual.  
  
-   Aunque el encabezado precompilado es de C\+\+, se está usando desde C.  Intente volver a compilar el encabezado para usarlo en C; para ello, especifique una de las opciones del compilador [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) o cambie el sufijo del archivo de origen a "c".  Para obtener más información, vea [Dos opciones para precompilar código](../../build/reference/two-choices-for-precompiling-code.md).