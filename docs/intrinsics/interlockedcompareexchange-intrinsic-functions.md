---
title: "_InterlockedCompareExchange Intrinsic Functions | Microsoft Docs"
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
  - "_InterlockedCompareExchange_HLERelease"
  - "_InterlockedCompareExchange8_nf"
  - "_InterlockedCompareExchange16_acq_cpp"
  - "_InterlockedCompareExchange_acq_cpp"
  - "_InterlockedCompareExchange16_rel_cpp"
  - "_InterlockedCompareExchange64_rel_cpp"
  - "_InterlockedCompareExchange_cpp"
  - "_InterlockedCompareExchange16_cpp"
  - "_InterlockedCompareExchange64_acq_cpp"
  - "_InterlockedCompareExchange_acq"
  - "_InterlockedCompareExchange64_rel"
  - "_InterlockedCompareExchange64_nf"
  - "_InterlockedCompareExchange_rel_cpp"
  - "_InterlockedCompareExchange16_nf"
  - "_InterlockedCompareExchange8"
  - "_InterlockedCompareExchange64_np"
  - "_InterlockedCompareExchange16_rel"
  - "_InterlockedCompareExchange64_acq"
  - "_InterlockedCompareExchange8_rel"
  - "_InterlockedCompareExchange_HLEAcquire"
  - "_InterlockedCompareExchange64_HLERelease"
  - "_InterlockedCompareExchange64_cpp"
  - "_InterlockedCompareExchange_np"
  - "_InterlockedCompareExchange8_acq"
  - "_InterlockedCompareExchange16_acq"
  - "_InterlockedCompareExchange_rel"
  - "_InterlockedCompareExchange64_HLEAcquire"
  - "_InterlockedCompareExchange64"
  - "_InterlockedCompareExchange16"
  - "_InterlockedCompareExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedCompareExchange intrinsic"
  - "_InterlockedCompareExchange_acq intrinsic"
  - "_InterlockedCompareExchange_rel intrinsic"
  - "_InterlockedCompareExchange16 intrinsic"
  - "_InterlockedCompareExchange64 intrinsic"
  - "_InterlockedCompareExchange64_acq intrinsic"
  - "_InterlockedCompareExchange64_rel intrinsic"
  - "InterlockedCompareExchange intrinsic"
  - "InterlockedCompareExchange_acq intrinsic"
  - "InterlockedCompareExchange_rel intrinsic"
  - "InterlockedCompareExchange16 intrinsic"
  - "InterlockedCompareExchange64 intrinsic"
  - "InterlockedCompareExchange64_acq intrinsic"
  - "InterlockedCompareExchange64_rel intrinsic"
ms.assetid: c3ad79c0-a523-4930-a3a4-69a65d7d5c81
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedCompareExchange Intrinsic Functions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realiza una comparación e intercambio entrelazados.  
  
## Sintaxis  
  
```  
long _InterlockedCompareExchange(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_acq(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_HLEAcquire(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_HLERelease(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_np(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_rel(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
char _InterlockedCompareExchange8(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_acq(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_nf(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_rel(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
short _InterlockedCompareExchange16(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_acq(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_nf(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_np(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_rel(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
__int64 _InterlockedCompareExchange64(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_acq(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_HLEAcquire (  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_HLERelease(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_nf(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_np(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_rel(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
```  
  
#### Parámetros  
 \[in, out\] `Destination`  
 Puntero al valor de destino.  El signo se omite.  
  
 \[in\] `Exchange`  
 Valor de intercambio.  El signo se omite.  
  
 \[in\] `Comparand`  
 Valor que se compara con el destino.  El signo se omite.  
  
## Valor devuelto  
 El valor devuelto es el valor inicial del puntero `Destination`.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Encabezado|  
|------------------------|------------------|----------------|  
|`_InterlockedCompareExchange`, `_InterlockedCompareExchange8`, `_InterlockedCompareExchange16`, `_InterlockedCompareExchange64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchange_acq`, `_InterlockedCompareExchange_rel`, `_InterlockedCompareExchange8_acq`, `_InterlockedCompareExchange8_nf`, `_InterlockedCompareExchange8_rel`,`_InterlockedCompareExchange16_acq`, `_InterlockedCompareExchange16_nf`, `_InterlockedCompareExchange16_rel`, `_InterlockedCompareExchange64_acq`, `_InterlockedCompareExchange64_nf`, `_InterlockedCompareExchange64_rel`,|ARM|\<intrin.h\>|  
|`_InterlockedCompareExchange_np`, `_InterlockedCompareExchange16_np`, `_InterlockedCompareExchange64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchange_HLEAcquire`, `_InterlockedCompareExchange_HLERelease`, `_InterlockedCompareExchange64_HLEAcquire`, `_InterlockedCompareExchange64_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Comentarios  
 `_InterlockedCompareExchange` realiza una comparación atómica del valor `Destination` con el valor `Comparand`.  Si el valor `Destination` es igual al valor `Comparand`, el valor `Exchange` se almacena en la dirección especificada por `Destination`.  De lo contrario, no se realiza ninguna operación.  
  
 `_InterlockedCompareExchange` proporciona compatibilidad intrínseca con el compilador para la función [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedCompareExchange](http://msdn.microsoft.com/library/ms683560.aspx) de Win32.  
  
 Hay diversas variaciones en `_InterlockedCompareExchange` que varían en función de los tipos de datos que implican y de si se utiliza la liberación o la adquisición de semántica específica del procesador.  
  
 Mientras que la función `_InterlockedCompareExchange` opera con valores enteros largos, `_InterlockedCompareExchange8` opera con valores enteros de 8 bits, `_InterlockedCompareExchange16` opera con valores enteros cortos y `_InterlockedCompareExchange64` opera con valores enteros de 64 bits  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` para adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos ARM con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 Los intrínsecos con un sufijo `_np` \("sin captura previa"\) impiden que el compilador inserte una posible operación de captura previa.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## Ejemplo  
 En el ejemplo siguiente, se utiliza `_InterlockedCompareExchange` para la sincronización de subprocesos simple de bajo nivel.  El enfoque tiene sus limitaciones como base para la programación multiproceso; se presenta para ilustrar el uso normal de los intrínsecos entrelazados.  Para obtener mejores resultados, utilice la API de Windows.  Para obtener más información acerca de la programación multiproceso, consulte [Crear un programa Win32 multiproceso](../parallel/writing-a-multithreaded-win32-program.md).  
  
```  
// intrinExample.cpp  
// compile with: /EHsc /O2  
// Simple example of using _Interlocked* intrinsics to  
// do manual synchronization  
//  
// Add [-DSKIP_LOCKING] to the command line to disable  
// the locking. This will cause the threads to execute out  
// of sequence.  
  
#define _CRT_RAND_S  
  
#include "windows.h"  
  
#include <iostream>  
#include <queue>  
#include <intrin.h>  
  
using namespace std;  
  
// --------------------------------------------------------------------  
  
// if defined, will not do any locking on shared data  
//#define SKIP_LOCKING  
  
// A common way of locking using _InterlockedCompareExchange.  
// Please refer to other sources for a discussion of the many issues  
// involved. For example, this particular locking scheme performs well   
// when lock contention is low, as the while loop overhead is small and  
// locks are acquired very quickly, but degrades as many callers want  
// the lock and most threads are doing a lot of interlocked spinning.  
// There are also no guarantees that a caller will ever acquire the  
// lock.  
namespace MyInterlockedIntrinsicLock  
{  
    typedef unsigned LOCK, *PLOCK;  
  
#pragma intrinsic(_InterlockedCompareExchange, _InterlockedExchange)  
  
    enum {LOCK_IS_FREE = 0, LOCK_IS_TAKEN = 1};  
  
    void Lock(PLOCK pl)   
    {  
#if !defined(SKIP_LOCKING)  
        // If *pl == LOCK_IS_FREE, it is set to LOCK_IS_TAKEN  
        // atomically, so only 1 caller gets the lock.  
        // If *pl == LOCK_IS_TAKEN,  
        // the result is LOCK_IS_TAKEN, and the while loop keeps spinning.  
        while (_InterlockedCompareExchange((long *)pl,  
                                           LOCK_IS_TAKEN, // exchange  
                                           LOCK_IS_FREE)  // comparand  
               == LOCK_IS_TAKEN)  
        {  
            // spin!  
        }  
        // This will also work.  
        //while (_InterlockedExchange(pl, LOCK_IS_TAKEN) ==   
        //                             LOCK_IS_TAKEN)  
        //{  
        //    // spin!  
        //}  
  
        // At this point, the lock is acquired.  
#endif  
    }  
  
    void Unlock(PLOCK pl) {  
#if !defined(SKIP_LOCKING)  
        _InterlockedExchange((long *)pl, LOCK_IS_FREE);  
#endif  
    }  
}  
  
// ------------------------------------------------------------------  
  
// Data shared by threads  
  
queue<int> SharedQueue;  
MyInterlockedIntrinsicLock::LOCK SharedLock;  
int TicketNumber;  
  
// ------------------------------------------------------------------  
  
DWORD WINAPI  
ProducerThread(  
    LPVOID unused  
    )  
{  
    unsigned int randValue;  
    while (1) {  
        // Acquire shared data. Enter critical section.  
        MyInterlockedIntrinsicLock::Lock(&SharedLock);  
  
        //cout << ">" << TicketNumber << endl;  
        SharedQueue.push(TicketNumber++);  
  
        // Release shared data. Leave critical section.  
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);  
  
        rand_s(&randValue);  
        Sleep(randValue % 20);  
    }  
  
    return 0;  
}  
  
DWORD WINAPI  
ConsumerThread(  
    LPVOID unused  
    )  
{  
    while (1) {  
        // Acquire shared data. Enter critical section  
        MyInterlockedIntrinsicLock::Lock(&SharedLock);  
  
        if (!SharedQueue.empty()) {  
            int x = SharedQueue.front();  
            cout << "<" << x << endl;  
            SharedQueue.pop();  
        }  
  
        // Release shared data. Leave critical section  
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);  
  
        unsigned int randValue;  
        rand_s(&randValue);  
        Sleep(randValue % 20);  
    }  
    return 0;  
}  
  
int main(  
    void  
    )  
{  
    const int timeoutTime = 500;  
    int unused1, unused2;  
    HANDLE threads[4];  
  
    // The program creates 4 threads:  
    // two producer threads adding to the queue  
    // and two consumers taking data out and printing it.  
    threads[0] = CreateThread(NULL,  
                              0,  
                              ProducerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[1] = CreateThread(NULL,  
                              0,  
                              ConsumerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[2] = CreateThread(NULL,  
                              0,  
                              ProducerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[3] = CreateThread(NULL,  
                              0,  
                              ConsumerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    WaitForMultipleObjects(4, threads, TRUE, timeoutTime);  
  
    return 0;  
}  
```  
  
  **\<0**  
**\<1**  
**\<2**  
**\<3**  
**\<4**  
**\<5**  
**\<6**  
**\<7**  
**\<8**  
**\<9**  
**\<10**  
**\<11**  
**\<12**  
**\<13**  
**\<14**  
**\<15**  
**\<16**  
**\<17**  
**\<18**  
**\<19**  
**\<20**  
**\<21**  
**\<22**  
**\<23**  
**\<24**  
**\<25**  
**\<26**  
**\<27**  
**\<28**  
**\<29**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_InterlockedCompareExchange128](../intrinsics/interlockedcompareexchange128.md)   
 [Funciones intrínsecas \_InterlockedCompareExchangePointer](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)