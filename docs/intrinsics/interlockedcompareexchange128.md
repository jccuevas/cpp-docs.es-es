---
title: "_InterlockedCompareExchange128 | Microsoft Docs"
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
  - "_InterlockedCompareExchange128_cpp"
  - "_InterlockedCompareExchange128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cmpxchg16b (instrucción)"
  - "_InterlockedCompareExchange128 (función intrínseca)"
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedCompareExchange128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realiza 128 que el bit entrelazado compara y cambiar.  
  
## Sintaxis  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### Parámetros  
 \[in, out\] `Destination`  
 Puntero al destino, que es una matriz de dos enteros de 64 bits en como campo de bits 128.  Los datos de destino deben ser el 16 bytes alineado evitar un error de protección general.  
  
 \[in\] `ExchangeHigh`  
 Un entero de 64 bits que se puede cambiar con gran parte de destino.  
  
 \[in\] `ExchangeLow`  
 Un entero de 64 bits que se puede cambiar con la parte baja de destino.  
  
 \[in, out\] `ComparandResult`  
 Puntero a una matriz de dos enteros de 64 bits \(considerados como campo de bits 128\) que se va a comparar con el destino.  En la salida, esto se sobrescribe con el valor original del destino.  
  
## Valor devuelto  
 1 si el término de una comparación de 128 bits es igual al valor original de destino.  `ExchangeHigh` y `ExchangeLow` sobrescriben el destino de 128 bits.  
  
 0 si el término de una comparación no es igual al valor original de destino.  El destino no cambia y el valor del término de una comparación se sobrescribe con el valor de destino.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de`cmpxchg16b` \(con el prefijo de `lock` \) de realizar 128 al bit bloqueado compara y cambiar.  Las versiones tempranas de hardware de 64 bits de AMD no admiten esta instrucción.  Para comprobar la compatibilidad de hardware para la instrucción de `cmpxchg16b`, llame a intrínsecos de `__cpuid` con `InfoType=0x00000001 (standard function 1)`.  El bit 13 de `CPUInfo[2]`\(ECX\) es 1 si se admite la instrucción.  
  
> [!NOTE]
>  El valor de `ComparandResult` se sobrescribe siempre.  Después de la instrucción de `lock` , este intrínseco inmediatamente copia el valor inicial de `Destination` a `ComparandResult`.  Por esta razón, `ComparandResult` y `Destination` deben designar para separar ubicaciones de memoria para evitar un comportamiento inesperado.  
  
 Aunque puede utilizar `_InterlockedCompareExchange128` para la sincronización de bajo nivel de subproceso, no es necesario sincronizar sobre 128 bits si puede utilizar funciones más pequeñas de sincronización \(como los demás intrínsecos de `_InterlockedCompareExchange` \) en su lugar.  Utilice `_InterlockedCompareExchange128` si desea acceso atómico en un valor de 128 bits en memoria.  
  
 Si ejecuta el código que utiliza este intrínseco en el hardware que no admite la instrucción de `cmpxchg16b` , los resultados son imprevisibles.  
  
 Esta rutina solo está disponible como intrínseco.  
  
## Ejemplo  
 Este ejemplo utiliza `_InterlockedCompareExchange128` para reemplazar la alta palabra de una matriz de dos enteros de 64 bits con la suma de las palabras de máximo y mínimo y aumentar la palabra baja.  El acceso a la matriz de BigInt.Int es atómico, pero este ejemplo utiliza un único subproceso y omite el bloqueo para simplificar.  
  
```  
// cmpxchg16b.c  
// processor: x64  
// compile with: /EHsc /O2  
#include <stdio.h>  
#include <intrin.h>  
  
typedef struct _LARGE_INTEGER_128 {  
    __int64 Int[2];  
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;  
  
volatile LARGE_INTEGER_128 BigInt;  
  
// This AtomicOp() function atomically performs:  
//   BigInt.Int[1] += BigInt.Int[0]  
//   BigInt.Int[0] += 1  
void AtomicOp ()  
{  
    LARGE_INTEGER_128 Comparand;  
    Comparand.Int[0] = BigInt.Int[0];  
    Comparand.Int[1] = BigInt.Int[1];  
    do {  
        ; // nothing  
    } while (_InterlockedCompareExchange128(BigInt.Int,  
                                            Comparand.Int[0] + Comparand.Int[1],  
                                            Comparand.Int[0] + 1,  
                                            Comparand.Int) == 0);  
}  
  
// In a real application, several threads contend for the value  
// of BigInt.  
// Here we focus on the compare and exchange for simplicity.  
int main(void)  
{  
   BigInt.Int[1] = 23;  
   BigInt.Int[0] = 11;  
   AtomicOp();  
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",  
      BigInt.Int[1],BigInt.Int[0]);  
}  
```  
  
  **BigInt.Int \[1\] \= 34, BigInt.Int \[0\] \= 12**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_InterlockedCompareExchange Intrinsic Functions](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)