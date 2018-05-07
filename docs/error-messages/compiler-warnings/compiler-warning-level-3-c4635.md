---
title: Compilador advertencia (nivel 3) C4635 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2dcc4b7466ed53a187b7f34ec45084a94adb59b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4635"></a>Advertencia del compilador (nivel 3) C4635
destino del comentario del documento XML: XML incorrectamente formado: motivo  
  
 El compilador encontró algún problema con las etiquetas XML.  Corrija el problema y vuelva a compilar  
  
 El ejemplo siguiente genera la advertencia C4635:  
  
```  
// C4635.cpp  
// compile with: /doc /clr /W3 /c  
/// <summary>     
/// The contents of the folder have changed.  
/// <summary/>   // C4635  
  
// try the following line instead  
// /// </summary>  
public ref class Test {};  
```  
  
 Observe que la salida de este ejemplo indica: **La etiqueta final 'member' no coincide con la etiqueta inicial 'summary'**.  
  
 El problema con este ejemplo es que la etiqueta de cierre para \<resumen > está incorrectamente formada y el compilador no la reconoce como el \<resumen > etiqueta de cierre.  El \<miembro > incrusta la etiqueta en el archivo .xdc mediante el compilador en cada compilación/doc.  Por lo tanto, el problema es que la etiqueta de cierre \</member >, no coincide con la etiqueta inicial anterior que el compilador ha procesado (\<resumen >.