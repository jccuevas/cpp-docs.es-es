---
title: "Advertencia del compilador (nivel 4) C4985 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4985"
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4985
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol name': atributos no presentes en la declaración anterior.  
  
 Las anotaciones de lenguaje de anotación de código fuente \(SAL\) de Microsoft en la definición o declaración de método actual se diferencian de las anotaciones en una declaración anterior. Las mismas anotaciones SAL deben usarse en la definición y las declaraciones de un método.  
  
 El lenguaje SAL proporciona un conjunto de anotaciones que puede usar para describir la forma en que una función usa sus parámetros, las hipótesis que realiza sobre estos y las garantías que ofrece al final. Las anotaciones se definen en el archivo de encabezado sal.h.  
  
 Observe que las macros SAL no se expandirán a menos que el proyecto tenga el marcador [\/analyze](../../build/reference/analyze-code-analysis.md) especificado. Si especifica **\/analyze**, el compilador puede generar la advertencia C4985, aunque ningún error o advertencia apareciese sin **\/analyze**.  
  
### Para corregir este error  
  
1.  Use las mismas anotaciones SAL en la definición de un método y en todas sus declaraciones.  
  
## Vea también  
 [Anotaciones de SAL](../../c-runtime-library/sal-annotations.md)