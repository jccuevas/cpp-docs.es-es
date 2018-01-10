---
title: Compilador advertencia (nivel 4) C4001 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4001
dev_langs: C++
helpviewer_keywords: C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3b5c3d82bef81ee84514b39a0ce8ab07ad6e6c36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4001"></a>Compilador advertencia (nivel 4) C4001
se usó una extensión no estándar 'comentario de una única línea'  

> [!NOTE] 
> Esta advertencia se ha eliminado en Visual Studio 2017 versión 15,5 ya son estándar de C99 comentarios de una línea.
  
 Los comentarios de línea son estándar en C++ y estándar de C a partir de C99. Compatibilidad estricta con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), archivos de C que contienen comentarios de una línea, generan C4001 debido al uso de una extensión no estándar. Puesto que los comentarios de línea son estándar en C++, archivos de C que contienen comentarios de una línea no generan C4001 al compilar con extensiones de Microsoft (/Ze).  
  
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