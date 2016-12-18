---
title: "Informaci&#243;n general del ensamblador alineado | Microsoft Docs"
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
  - "__asm (palabra clave) [C++], invocar ensamblador alineado"
  - "ensamblador alineado"
  - "ensamblado en línea, ensamblador alineado"
  - "invocar ensamblador alineado"
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Informaci&#243;n general del ensamblador alineado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El ensamblador alineado permite incrustar instrucciones de lenguaje de ensamblado directamente en los programas de origen de C y C\+\+ sin realizar pasos adicionales de ensamblado y vinculación.  El ensamblador alineado se compila en el compilador; por lo tanto, no se necesita un ensamblador independiente como Microsoft Macro Assembler \(MASM\).  
  
 Dado que el ensamblador alineado no requiere pasos de ensamblado y vínculo independientes y de vínculo, es más aconsejable que un ensamblador independiente.  El código de ensamblado alineado puede utilizar cualquier nombre de variable o de función de C o C\+\+ que esté en el ámbito, por lo que resulta fácil integrarlo con el código C o C\+\+ del programa.  Y, dado que el código de ensamblado se puede combinar con instrucciones de C o C\+\+, puede realizar tareas complicadas o imposibles solo en C o C\+\+.  
  
 La palabra clave [\_\_asm](../../assembler/inline/asm.md) invoca el ensamblador alineado y puede aparecer siempre que una instrucción de C o C\+\+ sea válida.  No puede aparecer por sí sola.  Debe ir seguida de una instrucción de ensamblado, un grupo de instrucciones entre llaves o, como mínimo, un par de llaves vacío.  El término "bloque `__asm`" aquí hace referencia a cualquier instrucción o grupo de instrucciones, incluido o no entre llaves.  
  
 El código siguiente es un bloque `__asm` simple incluido entre llaves. \(El código es una secuencia de prólogo de función personalizada\).  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
}  
```  
  
 Como alternativa, puede colocar `__asm` delante de cada instrucción de ensamblado:  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 Dado que la palabra clave `__asm` es un separador de la instrucción, también puede colocar las instrucciones de ensamblado en la misma línea:  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)