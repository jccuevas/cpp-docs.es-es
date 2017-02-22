---
title: "Error del compilador C3859 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3859"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3859"
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3859
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '\-Zmvalue' o superior  
  
 El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él.  Use la marca de compilador **\/Zm** para especificar un valor mayor para el archivo de encabezado precompilado.  Para obtener más información, vea [\/Zm \(Especificar el límite de asignación de memoria del encabezado precompilado\)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).