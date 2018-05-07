---
title: _ReturnAddress | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0431302ae745a1e4a03da4b3fd660fda7d2cfa72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El `_ReturnAddress` intrínseco proporciona la dirección de la instrucción de la función que realiza la llamada que se ejecutará después de que el control vuelve al llamador.  
  
 Compile el siguiente programa y paso a través de él en el depurador. Paso a paso a través del programa, tenga en cuenta la dirección que se devuelve desde `_ReturnAddress`. A continuación, inmediatamente después de volver de la función donde `_ReturnAddress` se ha usado, abra el [Cómo: utilizar la ventana Desensamblado](/visualstudio/debugger/how-to-use-the-disassembly-window) y tenga en cuenta que la dirección de la siguiente instrucción que se ejecuta coincide con la dirección devuelta de `_ReturnAddress`.  
  
 Optimizaciones tales como la inclusión puede afectar a la dirección de retorno. Por ejemplo, si el programa de ejemplo siguiente se compila con [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` se insertarán entre líneas a la función que realiza la llamada, `main`. Por lo tanto, las llamadas a `_ReturnAddress` de `inline_func` y `main` cada una, se producirá el mismo valor.  
  
 Cuando `_ReturnAddress` se utiliza en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene el `_ReturnAddress` llamada se compilará como una función nativa. Cuando se compila una función como administrado llama a la función que contiene `_ReturnAddress`, `_ReturnAddress` puede que no funcione según lo previsto.  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="example"></a>Ejemplo  
  
```  
// compiler_intrinsics__ReturnAddress.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_ReturnAddress)  
  
__declspec(noinline)  
void noinline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
__forceinline  
void inline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
int main(void)  
{  
   noinline_func();   
   inline_func();  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
  
   return 0;  
}  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)