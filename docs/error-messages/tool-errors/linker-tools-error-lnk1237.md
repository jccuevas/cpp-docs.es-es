---
title: Las herramientas del vinculador LNK1237 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ffc337d6b1548db4717dc4b87ff8aa25ef92e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1237"></a>Error de las herramientas del vinculador LNK1237
durante la generación de código, el compilador ha introducido referencia al símbolo 'symbol' definido en el módulo 'module' compilado con/GL  
  
 Durante la generación de código, el compilador no debe introducir los símbolos que se resuelven más adelante a definiciones compiladas **/GL**. `symbol` es un símbolo que se ha introducido y posteriormente resuelto con una definición compilada con **/GL**.  
  
 Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).  
  
 Para resolver LNK1237, no compile el símbolo con **/GL** o use [/INCLUDE (forzar referencias de símbolos)](../../build/reference/include-force-symbol-references.md) para forzar una referencia al símbolo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error LNK1237. Para resolver este error, no inicialice la matriz en LNK1237_a.cpp y agregue **/ include: __chkstk** para el comando de link.  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```