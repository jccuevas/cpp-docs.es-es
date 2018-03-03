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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 528147eceadd35cc0d9fe656bdc7ce7965339a0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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