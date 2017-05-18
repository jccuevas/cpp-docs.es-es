---
title: Compilador advertencia (nivel 4) C4001 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bbcf2db5f6650bd9118b28c8bbfe921d13306410
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4001"></a>Compilador advertencia (nivel 4) C4001
se ha utilizado la extensión de tipo no estándar 'comentario de una sola línea'  
  
 Los comentarios de línea son estándar en C++ y no estándar en C. Compatibilidad estricta con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), los archivos de C que contienen comentarios de una línea, generan C4001 debido al uso de una extensión no estándar. Dado que los comentarios de línea son estándar en C++, los archivos de C que contienen comentarios de una línea no producen C4001 al compilar con extensiones de Microsoft (/Ze).  
  
## <a name="example"></a>Ejemplo  
 Para deshabilitar la advertencia, quite la marca de comentario [warning(disable:4001) #pragma](../../preprocessor/warning.md).  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```
