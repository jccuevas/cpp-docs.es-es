---
title: "float_control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.float_control"
  - "float_control_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "float_control (pragma)"
  - "pragma (directivas), float_control"
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 11
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# float_control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el comportamiento de punto flotante de una función.  
  
## Sintaxis  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## Marcas  
 `value` *,* `setting` **\[push\]**  
 Especifica un comportamiento de punto flotante.  `value` puede ser **precise** o **except**.  Para obtener más información, vea [\/fp \(Especificar comportamiento de punto flotante\)](../build/reference/fp-specify-floating-point-behavior.md).  `setting` puede ser **on** u **off**.  
  
 Si `value` es **precise**, se especifican los valores de **precise** y **except** .  **except** solo se puede establecer en **on** cuando **precise** también se establece en **on**.  
  
 Si se agrega el token opcional **push** , el valor actual de `value` se inserta en la pila interna del compilador.  
  
 **push**  
 Inserta el valor de `float_control` actual en la pila interna del compilador.  
  
 **pop**  
 Quita el valor de`float_control` de la parte superior de la pila interna del compilador y lo convierte en el nuevo valor de `float_control`.  
  
## Comentarios  
 No puede desactivar `float_control precise` cuando **except** está activado.  De igual forma, **precise** no se puede desactivar cuando `fenv_access` está activado.  Para pasar del modelo estricto a un modelo rápido con la instrucción pragma `float_control`, utilice el código siguiente:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
// The following line is needed on Itanium processors  
#pragma fp_contract(on)  
```  
  
 Para pasar del modelo rápido a un modelo estricto con la instrucción pragma `float_control`, utilice el código siguiente:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
// The following line is needed on Itanium processors.  
#pragma fp_contract(off)  
```  
  
 Las directivas pragma de punto flotante incluyen:  
  
-   [fenv\_access](../preprocessor/fenv-access.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo detectar una excepción de desbordamiento de punto flotante mediante la instrucción pragma `float_control`.  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
  **Sin errores**   
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)