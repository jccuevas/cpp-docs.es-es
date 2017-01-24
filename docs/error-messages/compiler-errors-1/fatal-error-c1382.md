---
title: "Error irrecuperable C1382 | Microsoft Docs"
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
  - "C1382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1382"
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el archivo PCH 'archivo' se ha recompilado desde que se creó 'obj'.Recompile este objeto  
  
 Al utilizar [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md), el compilador ha detectado un archivo .pch más reciente que un archivo .obj CIL que hace referencia al primero.  La información del archivo .obj CIL no está actualizada.  Recompile el objeto.  
  
 C1382 puede ocurrir, asimismo, si se compila con **\/Yc**, pero también se pasan varios archivos de código fuente al compilador.  Para resolverlo, no utilice **\/Yc** al pasar varios archivos de código fuente al compilador.  Para obtener más información, vea [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md).