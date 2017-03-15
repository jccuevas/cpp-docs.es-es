---
title: "Error del compilador C2017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2017"
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

secuencia de escape no válida  
  
 Hay una secuencia de escape \(como \\t\) fuera de una constante de caracteres o de cadena.  
  
 El código siguiente genera el error C2017:  
  
```  
// C2017.cpp  
int main() {  
   char test1='a'\n;   // C2017  
   char test2='a\n';   // ok  
}  
```  
  
 Puede producirse el error C2017 cuando el operador de generación de cadenas se utiliza con cadenas que incluyen secuencias de escape.  
  
 El código siguiente genera el error C2017:  
  
```  
// C2017b.cpp  
#define TestDfn(x) AfxMessageBox(#x)  
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017  
```