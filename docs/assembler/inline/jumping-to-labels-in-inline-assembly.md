---
title: "Saltar a etiquetas en un ensamblado alineado | Microsoft Docs"
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
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], etiquetas"
  - "distinción de mayúsculas y minúsculas, etiquetas en ensamblado alineado"
  - "ensamblado en línea, saltar a etiquetas"
  - "saltar a etiquetas en ensamblado alineado"
  - "etiquetas, en bloques __asm"
  - "etiquetas, en ensamblado alineado"
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Saltar a etiquetas en un ensamblado alineado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Como una etiqueta normal de C o C\+\+, una etiqueta en un bloque `__asm` tiene su ámbito en toda la función en la que se define \(no solo en el bloque\).  Las instrucciones de ensamblado y las instrucciones `goto` pueden saltar a las etiquetas dentro o fuera del bloque `__asm`.  
  
 Las etiquetas definidas en los bloques `__asm` no distinguen entre mayúsculas y minúsculas; las instrucciones `goto` e instrucciones de ensamblado pueden hacer referencia a esas etiquetas sin tener en cuenta el uso de mayúsculas y minúsculas.  Las etiquetas de C y C\+\+ distinguen entre mayúsculas y minúsculas cuando se utilizan en las instrucciones `goto`.  Las instrucciones de ensamblado pueden saltar a una etiqueta de C o C\+\+ sin tener en cuenta el uso de mayúsculas y minúsculas.  
  
 El código siguiente muestra todas las permutaciones:  
  
```  
void func( void )  
{  
   goto C_Dest;  /* Legal: correct case   */  
   goto c_dest;  /* Error: incorrect case */  
  
   goto A_Dest;  /* Legal: correct case   */  
   goto a_dest;  /* Legal: incorrect case */  
  
   __asm  
   {  
      jmp C_Dest ; Legal: correct case  
      jmp c_dest ; Legal: incorrect case  
  
      jmp A_Dest ; Legal: correct case  
      jmp a_dest ; Legal: incorrect case  
  
      a_dest:    ; __asm label  
   }  
  
   C_Dest:       /* C label */   
   return;  
}  
int main()  
{  
}  
```  
  
 No utilice nombres de función de biblioteca de C como etiquetas en los bloques `__asm`.  Por ejemplo, podría verse tentado a utilizar `exit` como etiqueta, como sigue:  
  
```  
; BAD TECHNIQUE: using library function name as label  
jne exit  
   .  
   .  
   .  
exit:  
   ; More __asm code follows  
```  
  
 Dado que **exit** es el nombre de una función de biblioteca de C, este código podría producir un salto a la función **exit** en lugar de a la ubicación deseada.  
  
 Como sucede en los programas MASM, el símbolo de dólar \(`$`\) sirve de contador para la ubicación actual.  Es una etiqueta para la instrucción que se ensambla actualmente.  En los bloques `__asm`, su uso principal es crear saltos condicionales largos:  
  
```  
jne $+5 ; next instruction is 5 bytes long  
jmp farlabel  
; $+5  
   .  
   .  
   .  
farlabel:  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)