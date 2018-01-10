---
title: Error del compilador C3382 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3382
dev_langs: C++
helpviewer_keywords: C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c58047e409c60fd2b6cb65418131f6aadb1430a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3382"></a>Error del compilador C3382
'sizeof' no se admite con /clr:safe  
  
 El archivo de resultados de una compilación **/clr:safe** es un archivo de seguridad de tipos comprobable y el operador sizeof no se admite porque el valor devuelto del operador sizeof es size_t, cuyo tamaño varía según el sistema operativo.  
  
 Para obtener más información, vea  
  
-   [sizeof (operador)](../../cpp/sizeof-operator.md)  
  
-   [/CLR (compilación de common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3382:  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```