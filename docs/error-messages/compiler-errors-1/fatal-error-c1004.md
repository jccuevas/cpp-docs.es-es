---
title: Error irrecuperable C1004 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88f76c00c8f5b36acf238f0da88e908eac6dbe8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197174"
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
  
 Posible resolución:  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```