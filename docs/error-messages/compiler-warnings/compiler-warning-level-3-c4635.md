---
title: Compilador advertencia (nivel 3) C4635 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b6a19618afeed952cfa594961a0e4ccb777d26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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