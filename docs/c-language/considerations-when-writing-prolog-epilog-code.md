---
title: "Consideraciones para escribir c&#243;digo de pr&#243;logo y ep&#237;logo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__LOCAL_SIZE (constante)"
  - "diseños, marco de pila"
  - "diseño de marco de pila"
  - "pila, diseño de marco de pila"
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Consideraciones para escribir c&#243;digo de pr&#243;logo y ep&#237;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Antes de escribir sus propias secuencias de código de prólogo y epílogo, es importante que comprenda cómo se diseña el marco de pila.  También es útil saber utilizar la constante predefinida **\_\_LOCAL\_SIZE**.  
  
##  <a name="_clang_c_stack_frame_layout"></a> Diseño del marco de pila de C  
 En este ejemplo se muestra el código de prólogo estándar que puede aparecer en una función de 32 bits:  
  
```  
push     ebp                 ; Save ebp  
mov      ebp, esp            ; Set stack frame pointer  
sub      esp, localbytes     ; Allocate space for locals  
push     <registers>         ; Save registers  
```  
  
 La variable `localbytes` representa el número de bytes necesarios en la pila para las variables locales y la variable `registers` es un marcador de posición que representa la lista de registros que se guarden en la pila.  Después de insertar los registros, puede colocar cualquier otro dato adecuado en la pila.  A continuación, se muestra el código de epílogo correspondiente:  
  
```  
pop      <registers>         ; Restore registers  
mov      esp, ebp            ; Restore stack pointer  
pop      ebp                 ; Restore ebp  
ret                          ; Return from function  
```  
  
 La pila siempre va de mayor a menor \(de las direcciones de memoria superiores a las inferiores\).  El puntero base \(`ebp`\) señala al valor insertado de `ebp`.  El área de variables locales comienza en `ebp-2`.  Para tener acceso a las variables locales, calcule un desplazamiento de `ebp` restando el valor apropiado a `ebp`.  
  
##  <a name="_clang_the___local_size_constant"></a> La constante \_\_LOCAL\_SIZE  
 El compilador proporciona una constante, **\_\_LOCAL\_SIZE**, para su uso en el bloque de ensamblador alineado del código de prólogo de la función.  Esta constante se utiliza para asignar espacio para las variables locales del marco de pila en código de prólogo personalizado.  
  
 El compilador determina el valor de **\_\_LOCAL\_SIZE**.  El valor es el número total de bytes de todas las variables locales definidas por el usuario y las variables temporales generadas por el compilador.  **\_\_LOCAL\_SIZE** se puede utilizar como operando inmediato; no se puede utilizar en una expresión.  No debe cambiar o volver a definir el valor de esta constante.  Por ejemplo:  
  
```  
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov      eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 En el ejemplo siguiente de una función naked que contiene secuencias personalizadas de prólogo y de epílogo se utiliza **\_\_LOCAL\_SIZE** en la secuencia de prólogo:  
  
```  
__declspec ( naked ) func()  
{  
   int i;  
   int j;  
  
   __asm      /* prolog */  
      {  
      push   ebp  
      mov      ebp, esp  
      sub      esp, __LOCAL_SIZE  
      }  
  
   /* Function body */  
  
   __asm      /* epilog */  
      {  
      mov      esp, ebp  
      pop      ebp  
      ret  
      }  
}     
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Naked \(Funciones\)](../c-language/naked-functions.md)