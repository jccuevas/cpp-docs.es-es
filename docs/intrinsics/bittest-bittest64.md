---
title: "_bittest, _bittest64 | Microsoft Docs"
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
  - "_bittest64"
  - "_bittest_cpp"
  - "_bittest64_cpp"
  - "_bittest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bittest intrinsic"
  - "_bittest64 intrinsic"
  - "bt instruction"
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
caps.latest.revision: 19
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _bittest, _bittest64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción`bt`, que examina el bit en la posición `b` de la dirección `a` y devuelve el valor de ese bit.  
  
## Sintaxis  
  
```  
unsigned char _bittest(    long *a,    long b ); unsigned char _bittest64(    __int64 *a,    __int64 b );  
```  
  
#### Parámetros  
 \[in\] `a`  
 Puntero a la memoria que se va a examinar.  
  
 \[in\] `b`  
 La posición de bit que se va a probar.  
  
## Valor devuelto  
 El bit en la posición especificada.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_bittest`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_bittest64`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## Ejemplo  
  
```  
// bittest.cpp  
// processor: x86, ARM, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
long num = 78002;  
  
int main()  
{  
    unsigned char bits[32];  
    long nBit;  
  
    printf_s("Number: %d\n", num);  
  
    for (nBit = 0; nBit < 31; nBit++)  
    {  
        bits[nBit] = _bittest(&num, nBit);  
    }  
  
    printf_s("Binary representation:\n");  
    while (nBit--)  
    {  
        if (bits[nBit])  
            printf_s("1");  
        else  
            printf_s("0");  
    }  
}  
```  
  
  **Número: 78002**  
**Representación binaria:**  
**0000000000000010011000010110010**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)