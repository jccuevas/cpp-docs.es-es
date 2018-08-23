---
title: float_control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545852"
---
# <a name="floatcontrol"></a>float_control
Especifica el comportamiento de punto flotante de una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Marcas  
 
*valor*, *configuración* *[insertar]*  
Especifica un comportamiento en punto flotante. *valor* puede ser `precise` o `except`. Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md). *establecer* puede estar `on` o `off`.  
  
Si *valor* es `precise`, la configuración de `precise` y `except` se especifican. `except` solo se puede establecer en `on` cuando `precise` también se establece en `on`.  
  
Si el elemento opcional *inserción* token se agrega actual para *valor* se inserta en la pila interna del compilador.  
  
*push*  
Insertar actual **float_control** configuración de sesión en la pila interna del compilador  
  
*pop*  
Quita el **float_control** de la parte superior de la pila interna del compilador y hace que el nuevo **float_control** configuración.  
  
## <a name="remarks"></a>Comentarios  
 
No puede desactivar `float_control precise` cuando `except` está activado. De igual forma, `precise` no se puede desactivar cuando `fenv_access` está activado. Para pasar del modelo estricto a un modelo rápido con la **float_control** pragma, use el código siguiente:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
Para pasar del modelo rápido a un modelo estricto con la **float_control** pragma, use el código siguiente:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
Las directivas pragma de punto flotante incluyen:  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Ejemplo  
 
El ejemplo siguiente muestra cómo detectar una excepción de punto flotante de desbordamiento mediante la instrucción pragma **float_control**.  
  
```cpp  
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
