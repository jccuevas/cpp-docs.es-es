---
title: "Error de las herramientas del vinculador LNK1237 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1237"
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Error de las herramientas del vinculador LNK1237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

durante la generación del código, el compilador introdujo la referencia al símbolo 'símbolo' definido en el módulo 'módulo' compilado con \/GL  
  
 Durante la generación del código, el compilador no debe introducir símbolos que se resuelven más adelante con las definiciones compiladas con **\/GL**.  `symbol` es un símbolo que se introdujo y más tarde se resolvió con una definición compilada con **\/GL**.  
  
 Para obtener más información, vea [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).  
  
 Para resolver LNK1237, no compile el símbolo con **\/GL** o use [\/INCLUDE \(Forzar referencias de símbolos\)](../../build/reference/include-force-symbol-references.md) para forzar una referencia al símbolo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK1237.  Para resolver este error, no inicialice la matriz en LNK1237\_a.cpp y agregue **\/include:\_\_chkstk** al comando de vínculo.  
  
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