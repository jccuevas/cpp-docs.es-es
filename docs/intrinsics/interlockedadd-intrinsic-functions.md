---
title: "Funciones intr&#237;nsecas _InterlockedAdd | Microsoft Docs"
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
  - "_InterlockedAdd64_acq_cpp"
  - "_InterlockedAdd64_acq"
  - "_InterlockedAdd_acq"
  - "_InterlockedAdd_nf"
  - "_InterlockedAdd64_rel"
  - "_InterlockedAdd64"
  - "_InterlockedAdd_cpp"
  - "_InterlockedAdd_rel_cpp"
  - "_InterlockedAdd_rel"
  - "_InterlockedAdd64_rel_cpp"
  - "_InterlockedAdd64_cpp"
  - "_InterlockedAdd_acq_cpp"
  - "_InterlockedAdd64_nf"
  - "_InterlockedAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínsecos _InterlockedAdd"
  - "Intrínsecos _InterlockedAdd_acq"
  - "Intrínsecos _InterlockedAdd_nf"
  - "Intrínsecos _InterlockedAdd_rel"
  - "Intrínsecos _InterlockedAdd64"
  - "Intrínsecos _InterlockedAdd64_acq"
  - "Intrínsecos _InterlockedAdd64_nf"
  - "Intrínsecos _InterlockedAdd64_rel"
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas _InterlockedAdd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realizar una suma atómica, lo que garantiza que la operación se realiza correctamente cuando varios subprocesos tienen acceso a una variable compartida.  
  
## Sintaxis  
  
```  
long _InterlockedAdd(    long volatile * Addend,    long Value ); long _InterlockedAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedAdd_rel(    long volatile * Addend,    long Value ); __int64 _InterlockedAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_nf (    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_rel(    __int64 volatile * Addend,    __int64 Value );  
```  
  
#### Parámetros  
 \[in, out\] `Addend`  
 Puntero al entero al que se agregará; lo reemplaza el resultado de la suma.  
  
 \[in\] `Value`  
 El valor que se va a agregar.  
  
## Valor devuelto  
 Ambas funciones devuelven el resultado de la suma.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_InterlockedAdd`|ARM|  
|`_InterlockedAdd_acq`|ARM|  
|`_InterlockedAdd_nf`|ARM|  
|`_InterlockedAdd_rel`|ARM|  
|`_InterlockedAdd64`|ARM|  
|`_InterlockedAdd64_acq`|ARM|  
|`_InterlockedAdd64_nf`|ARM|  
|`_InterlockedAdd64_rel`|ARM|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Las versiones de estas funciones con los sufijos `_acq` o `_rel` realizan una suma entrelazada tras la adquisición o la liberación de semántica.  La adquisición de semántica significa que el resultado de la operación resulta visible para todos los subprocesos y procesadores antes de cualquier lectura y escritura de memoria posterior.  La adquisición es útil al entrar en una sección crítica.  La liberación de semántica significa que todas las lecturas y escrituras de memoria resultan visibles a todos los subprocesos y procesadores antes de que sea visible el resultado de la operación.  La liberación es útil al salir de una sección crítica.  Los intrínsecos con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## Ejemplo  
  
```  
// interlockedadd.cpp  
// Compile with: /Oi /EHsc  
// processor: ARM  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAdd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FF0000;  
        long retval;  
        retval = _InterlockedAdd(&data1, data2);  
        printf("0x%x 0x%x 0x%x", data1, data2, retval);  
}  
```  
  
## Salida  
  
```  
0xffffff00 0xff0000 0xffffff00  
```  
  
## Ejemplo  
  
```  
// interlockedadd64.cpp  
// compile with: /Oi /EHsc  
// processor: ARM  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_InterlockedAdd64)  
  
int main()  
{  
        __int64 data1 = 0x0000FF0000000000;  
        __int64 data2 = 0x00FF0000FFFFFFFF;  
        __int64 retval;  
        cout << hex << data1 << " + " << data2 << " = " ;  
        retval = _InterlockedAdd64(&data1, data2);  
        cout << data1 << endl;  
        cout << "Return value: " << retval << endl;  
}  
```  
  
## Salida  
  
```  
ff0000000000 + ff0000ffffffff = ffff00ffffffff  
Return value: ffff00ffffffff  
```  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)