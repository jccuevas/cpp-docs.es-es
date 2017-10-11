---
title: Error irrecuperable C1004 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c6a9e74d7918e1cb2c9190c87f4f1ec75f89237b
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1004"></a>Error irrecuperable C1004
final de archivo inesperado encontrado  
  
 El compilador ha alcanzado el final de un archivo de código fuente sin resolver una construcción. El código puede que falten uno de los siguientes elementos:  
  
-   Una llave de cierre  
  
-   Un paréntesis de cierre  
  
-   Marcador de comentario de cierre (* /)  
  
-   Un punto y coma  
  
 Para resolver este error, compruebe lo siguiente:  
  
-   La unidad de disco predeterminada tiene suficiente espacio para archivos temporales, que requieren aproximadamente el doble de espacio que el archivo de origen.  
  
-   Un `#if` directiva que se evalúa como false carece un cierre `#endif` directiva.  
  
-   Un archivo de código fuente no termina con un retorno de carro y avance de línea.  
  
 El ejemplo siguiente genera C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 Posible solución:  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```
