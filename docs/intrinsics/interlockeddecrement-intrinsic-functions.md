---
title: "Funciones intr&#237;nsecas _InterlockedDecrement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedDecrement16_rel_cpp"
  - "_InterlockedDecrement16_acq_cpp"
  - "_InterlockedDecrement16_rel"
  - "_InterlockedDecrement64_acq"
  - "_InterlockedDecrement_nf"
  - "_InterlockedDecrement16_nf"
  - "_InterlockedDecrement64_rel_cpp"
  - "_InterlockedDecrement_rel_cpp"
  - "_InterlockedDecrement16_acq"
  - "_InterlockedDecrement64_acq_cpp"
  - "_InterlockedDecrement_rel"
  - "_InterlockedDecrement64_nf"
  - "_InterlockedDecrement16_cpp"
  - "_InterlockedDecrement64"
  - "_InterlockedDecrement_cpp"
  - "_InterlockedDecrement64_rel"
  - "_InterlockedDecrement16"
  - "_InterlockedDecrement"
  - "_InterlockedDecrement64_cpp"
  - "_InterlockedDecrement_acq"
  - "_InterlockedDecrement_acq_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _InterlockedDecrement"
  - "Intrínseco _InterlockedDecrement_acq"
  - "Intrínseco _InterlockedDecrement_nf"
  - "Intrínseco _InterlockedDecrement_rel"
  - "Intrínseco _InterlockedDecrement16"
  - "Intrínseco _InterlockedDecrement16_acq"
  - "Intrínseco _InterlockedDecrement16_nf"
  - "Intrínseco _InterlockedDecrement16_rel"
  - "Intrínseco _InterlockedDecrement64"
  - "Intrínseco _InterlockedDecrement64_acq"
  - "Intrínseco _InterlockedDecrement64_nf"
  - "Intrínseco _InterlockedDecrement64_rel"
  - "Intrínseco InterlockedDecrement"
  - "Intrínseco InterlockedDecrement_acq"
  - "Intrínseco InterlockedDecrement_rel"
  - "Intrínseco InterlockedDecrement16"
  - "Intrínseco InterlockedDecrement64"
  - "Intrínseco InterlockedDecrement64_acq"
  - "Intrínseco InterlockedDecrement64_rel"
ms.assetid: 5268fce3-86b5-4b2b-b96c-2e531a3fb9b5
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas _InterlockedDecrement
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Proporciona compatibilidad intrínseca con el compilador para la función [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] [InterlockedDecrement](http://msdn.microsoft.com/library/ms683580.aspx) de Win32.  
  
## Sintaxis  
  
```  
long _InterlockedDecrement(  
   long * lpAddend  
);  
long _InterlockedDecrement_acq(  
   long * lpAddend  
);  
long _InterlockedDecrement_rel(  
   long * lpAddend  
);  
long _InterlockedDecrement_nf(  
   long * lpAddend  
);  
short _InterlockedDecrement16(  
   short * lpAddend  
);  
short _InterlockedDecrement16_acq(  
   short * lpAddend  
);  
short _InterlockedDecrement16_rel(  
   short * lpAddend  
);  
short _InterlockedDecrement16_nf(  
   short * lpAddend  
);  
__int64 _InterlockedDecrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedDecrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedDecrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedDecrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### Parámetros  
 \[in, out\] `lpAddend`  
 Puntero a la variable que se va a disminuir.  
  
## Valor devuelto  
 El valor devuelto es el valor resultante disminuido.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_InterlockedDecrement`, `_InterlockedDecrement16`, `_InterlockedDecrement64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_InterlockedDecrement_acq`, `_InterlockedDecrement_rel`, `_InterlockedDecrement_nf`, `_InterlockedDecrement16_acq`, `_InterlockedDecrement16_rel`, `_InterlockedDecrement16_nf`, `_InterlockedDecrement64_acq`, `_InterlockedDecrement64_rel`, `_InterlockedDecrement64_nf`,|ARM|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Hay diversas variaciones en `_InterlockedDecrement` que varían en función de los tipos de datos que implican y de si se utiliza la liberación o la adquisición de semántica específica del procesador.  
  
 Mientras que la función `_InterlockedDecrement` opera con valores enteros de 32 bits, `_InterlockedDecrement16` opera con valores enteros de 16 bits y `_InterlockedDecrement64` opera con valores enteros de 64 bits.  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 La variable a la que apunta el parámetro `lpAddend` debe estar alineada en un límite de 32 bits; de lo contrario, esta función produce un error en sistemas x86 multiprocesadores y en sistemas que no son x86.  Para obtener más información, consulte [alinear](../cpp/align-cpp.md).  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## Ejemplo  
  
```  
// compiler_intrinsics_interlocked.cpp  
// compile with: /Oi  
#define _CRT_RAND_S  
  
#include <cstdlib>  
#include <cstdio>  
#include <process.h>  
#include <windows.h>  
  
// To declare an interlocked function for use as an intrinsic,  
// include intrin.h and put the function in a #pragma intrinsic   
// statement.  
#include <intrin.h>  
  
#pragma intrinsic (_InterlockedIncrement)  
  
// Data to protect with the interlocked functions.  
volatile LONG data = 1;  
  
void __cdecl SimpleThread(void* pParam);  
  
const int THREAD_COUNT = 6;  
  
int main() {  
   DWORD num;  
   HANDLE threads[THREAD_COUNT];  
   int args[THREAD_COUNT];  
   int i;  
  
   for (i = 0; i < THREAD_COUNT; i++) {  
     args[i] = i + 1;  
     threads[i] = reinterpret_cast<HANDLE>(_beginthread(SimpleThread, 0,   
                           args + i));  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
         // error creating threads  
         break;  
   }  
  
   WaitForMultipleObjects(i, threads, true, INFINITE);  
}  
  
// Code for our simple thread  
void __cdecl SimpleThread(void* pParam) {  
   int threadNum = *((int*)pParam);  
   int counter;  
   unsigned int randomValue;  
   unsigned int time;  
   errno_t err = rand_s(&randomValue);  
  
   if (err == 0) {  
      time = (unsigned int) ((double) randomValue / (double) UINT_MAX * 500);  
      while (data < 100) {  
         if (data < 100) {  
            _InterlockedIncrement(&data);  
            printf_s("Thread %d: %d\n", threadNum, data);  
         }  
  
         Sleep(time);   // wait up to half of a second  
      }  
   }  
  
   printf_s("Thread %d complete: %d\n", threadNum, data);  
}  
```  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)