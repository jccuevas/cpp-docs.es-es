---
title: "__ud2 | Microsoft Docs"
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
  - "__ud2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UD2 (instrucción)"
  - "__ud2 (función intrínseca)"
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ud2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera una instrucción definida.  
  
## Sintaxis  
  
```  
void __ud2();  
```  
  
## Comentarios  
 El procesador produce una excepción no válida del código de operación si ejecuta una instrucción definida.  
  
 La función de `__ud2` es equivalente a la instrucción máquina de `UD2` , y está disponible únicamente en modo kernel.  Para obtener más información, busque el documento, “Manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones,” en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__ud2`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Ejemplo  
 El ejemplo siguiente se ejecuta una instrucción sin definir, produce una excepción.  El controlador de excepciones modifique el código de retorno a desde cero a uno.  
  
```  
// __ud2_intrinsic.cpp  
#include <stdio.h>  
#include <intrin.h>  
#include <excpt.h>  
// compile with /EHa  
  
int main() {  
  
// Initialize the return code to 0.  
 int ret = 0;  
  
// Attempt to execute an undefined instruction.  
  printf("Before __ud2(). Return code = %d.\n", ret);  
  __try {   
  __ud2();   
  }  
  
// Catch any exceptions and set the return code to 1.  
  __except(EXCEPTION_EXECUTE_HANDLER){  
  printf("  In the exception handler.\n");  
  ret = 1;  
  }  
  
// Report the value of the return code.   
  printf("After __ud2().  Return code = %d.\n", ret);  
  return ret;  
}  
```  
  
  **Antes de \_\_ud2 \(\).**  
 **Código de retorno \= 0.**  
 **En el controlador de excepciones.**  
 **Después de \_\_ud2 \(\).**  
 **Código de retorno \= 1.**   
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)