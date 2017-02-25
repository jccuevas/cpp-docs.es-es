---
title: "fenv_access | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.fenv_access"
  - "fenv_access_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fenv_access (pragma)"
  - "pragma (directivas), fenv_access"
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# fenv_access
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deshabilita \(ON\) o habilita \(OFF\) las optimizaciones que podrían cambiar las pruebas de marcadores y cambios de modo.  
  
## Sintaxis  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## Comentarios  
 De forma predeterminada, `fenv_access` es OFF.  
  
 Para obtener más información sobre el comportamiento de punto flotante, vea [\/fp \(Especificar comportamiento de punto flotante\)](../build/reference/fp-specify-floating-point-behavior.md).  
  
 Las clases de optimización que están sujetas a `fenv_access` son:  
  
-   Eliminación común global de la subexpresión  
  
-   Movimiento de código  
  
-   Plegamiento constante  
  
 Las directivas pragma de punto flotante incluyen:  
  
-   [float\_control](../preprocessor/float-control.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## Ejemplo  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=9,999999776482582e\-003**   
## Ejemplo  
 El ejemplo siguiente es para un compilador que genera archivos de salida para procesadores Itanium.  **\/fp:precise** conserva los resultados intermedios con una precisión ampliada donde los valores mayores que FLT\_MAX \(3,402823466e\+38F\) se pueden calcular y, como resultado de esa suma, tendrán un resultado de 1,0, como si se calculasen manualmente.  **\/fp:strict** conserva los resultados intermedios en su precisión de origen \(float\) de modo que la primera suma genere un valor infinito, que se conserva en toda la expresión.  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
  **1.000000**   
## Ejemplo  
 Al marcar como comentario el fragmento `#pragma fenv_access (on)` del ejemplo anterior, observe que el resultado es diferente, porque el compilador realiza la evaluación en tiempo de compilación, que no utiliza el modo de control.  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=1.000000000000000e\-002**   
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)