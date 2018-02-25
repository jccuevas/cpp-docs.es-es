---
title: fenv_access | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f06c699ba20d09ec1d013f9464af02935da9f9c1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="fenvaccess"></a>fenv_access
Deshabilita (ON) o habilita (OFF) las optimizaciones que podrían cambiar las pruebas de marcadores y cambios de modo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, `fenv_access` es OFF.  
  
 Para obtener más información sobre el comportamiento de punto flotante, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).  
  
 Las clases de optimización que están sujetas a `fenv_access` son:  
  
-   Eliminación común global de la subexpresión  
  
-   Movimiento de código  
  
-   Plegamiento constante  
  
 Las directivas pragma de punto flotante incluyen:  
  
-   [float_control](../preprocessor/float-control.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
out=9.999999776482582e-003  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente es para un compilador que genera archivos de salida para procesadores Itanium. **/ fp: precisa** conserva los resultados intermedios con una precisión ampliada donde los valores mayores que FLT_MAX (3, 402823466e + 38F) se pueden calcular y como resultado de esa suma tendrá resultado de 1,0, como debería si se calcula de forma manual. **/ fp: strict** mantiene los resultados intermedios en su precisión de origen (float) para la primera suma genere un valor infinito, que se mantiene a lo largo de la expresión.  
  
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
  
```Output  
1.000000  
```  
  
## <a name="example"></a>Ejemplo  
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
  
```Output  
out=1.000000000000000e-002  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)