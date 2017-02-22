---
title: "Advertencia del compilador (nivel 3) C4635 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4635"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4635"
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 3) C4635
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

destino del comentario del documento XML: XML incorrectamente formado: motivo  
  
 El compilador encontró algún problema con las etiquetas XML.  Corrija el problema y vuelva a compilar  
  
 El ejemplo siguiente genera la advertencia C4635:  
  
```  
// C4635.cpp // compile with: /doc /clr /W3 /c /// <summary> /// The contents of the folder have changed. /// <summary/>   // C4635 // try the following line instead // /// </summary> public ref class Test {};  
```  
  
 Observe que la salida de este ejemplo indica: **La etiqueta final 'member' no coincide con la etiqueta inicial 'summary'**.  
  
 El problema de este ejemplo es que la etiqueta final \<summary\> está incorrectamente formada y el compilador no la reconoce como la etiqueta final \<summary\>.  El compilador incrusta la etiqueta \<miembro\> en el archivo .xdc en cada compilación \/doc.  Por lo tanto, el problema es que la etiqueta final \<\/member\> no coincide con la etiqueta inicial anterior que el compilador ha procesado \(\<summary\>\).