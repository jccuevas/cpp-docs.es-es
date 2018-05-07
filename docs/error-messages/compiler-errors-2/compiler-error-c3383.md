---
title: Error del compilador C3383 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b54eda0e29a9876da83b9e3da384a39b9345d5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3383"></a>Error del compilador C3383
'operator new' no se admite con /clr:safe  
  
 El archivo de salida de una compilación **/clr:safe** es un archivo de seguridad de tipos comprobable y no se admiten punteros.  
  
 Para obtener más información, vea  
  
-   [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3383.  
  
```  
// C3383.cpp  
// compile with: /clr:safe  
int main() {  
   char* pCharArray = new char[256];  // C3383  
}  
```