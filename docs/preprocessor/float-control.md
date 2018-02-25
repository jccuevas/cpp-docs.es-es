---
title: float_control | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1525b92b43a688cdec970c646613aa4474d44cc3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="floatcontrol"></a>float_control
Especifica el comportamiento de punto flotante de una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Marcas  
 `value`, `setting` **[push]**  
 Especifica un comportamiento en punto flotante. `value` puede ser **precisa** o **excepto**. Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md). `setting` puede ser **en** o **desactivar**.  
  
 Si `value` es **precisa**, la configuración de **precisa** y **excepto** se especifican. **excepto** sólo se puede establecer en **en** cuando **precisa** también se establece en **en**.  
  
 Si la parte opcional **inserción** símbolo (token) se agrega la actual configuración para `value` se inserta en la pila interna del compilador.  
  
 **push**  
 Inserta el valor de `float_control` actual en la pila interna del compilador.  
  
 **pop**  
 Quita el `float_control` de la parte superior de la pila interna del compilador y hace que el nuevo `float_control` configuración.  
  
## <a name="remarks"></a>Comentarios  
 No se puede activar `float_control precise` cuando **excepto** se encuentra en. De forma similar, **precisa** no se puede desactivar cuando `fenv_access` se encuentra en. Para pasar del modelo estricto a un modelo rápido con la instrucción pragma `float_control`, utilice el código siguiente:  
  
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
  
-   [fenv_access](../preprocessor/fenv-access.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Ejemplo  
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
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)