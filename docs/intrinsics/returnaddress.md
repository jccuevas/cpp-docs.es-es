---
title: "_ReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ReturnAddress (función intrínseca)"
  - "ReturnAddress (función intrínseca)"
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _ReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Función intrínseca de `_ReturnAddress` proporciona la dirección de la instrucción en la función de llamada que se ejecutará después de que el control vuelve al llamador.  
  
 Compile el programa y el paso siguientes a través de en el depurador.  Como se recorre el programa, anote la dirección que se devuelve de `_ReturnAddress`.  A continuación, inmediatamente después de cambiar de la función en la `_ReturnAddress` se utilizó, abra [Cómo: Utilizar la ventana Desensamblado](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md) y observe que la dirección de la siguiente instrucción de ser coincidencias ejecutadas que la dirección devolvió de `_ReturnAddress`.  
  
 Optimizaciones tales como la pueden afectar al de.  Por ejemplo, si el programa de ejemplo siguiente se compila con [\/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` está alineada en la función que llama, `main`.  Por tanto, las llamadas a `_ReturnAddress` de `inline_func` y a `main` se aplicará cada producen el mismo valor.  
  
 Cuando `_ReturnAddress` se utiliza en un programa compilado con [\/clr](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene la llamada de `_ReturnAddress` se compiló como función nativa.  Cuando una función compilada como llamadas administradas en la función que contiene `_ReturnAddress`, `_ReturnAddress` no puede comportarse como se espera.  
  
## Requisitos  
 **Archivo de encabezado** \<intrin.h\>  
  
## Ejemplo  
  
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
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)