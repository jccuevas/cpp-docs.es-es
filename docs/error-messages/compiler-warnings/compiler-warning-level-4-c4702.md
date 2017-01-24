---
title: "Advertencia del compilador (nivel 4) C4702 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4702"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4702"
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4702
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede tener acceso al código  
  
 Esta advertencia es el resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: código inalcanzable.  Cuando el compilador \(back end\) detecte código inalcanzable, generará la advertencia C4702, una advertencia de nivel 4.  
  
 Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, quite el código inalcanzable o asegúrese de que todo el código fuente es alcanzable por algún flujo de ejecución.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4702.  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## Ejemplo  
 Cuando se compila con **\/GX**, **\/EHc**, **\/EHsc** o  **\/EHac** utilizando funciones extern de C, el código puede ser inalcanzable porque las funciones de C no producen excepciones, por lo que el bloque catch no es alcanzable.   Si esta advertencia no es válida porque una función puede producir una excepción, compile con **\/EHa** o **\/EHs**, dependiendo de la excepción.  
  
 Para obtener más información, vea [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md).  
  
 El ejemplo siguiente genera el error C4702.  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```