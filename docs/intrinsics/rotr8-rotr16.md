---
title: "_rotr8, _rotr16 | Microsoft Docs"
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
  - "_rotr16"
  - "_rotr8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rotr16 intrinsic"
  - "_rotr8 intrinsic"
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rotr8, _rotr16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Girar los valores de entrada a la derecha hacia el bit menos significativo \(LSB\) según un número especificado de posiciones de bit.  
  
## Sintaxis  
  
```  
unsigned char _rotr8(     unsigned char value,     unsigned char shift  ); unsigned short _rotr16(     unsigned short value,     unsigned char shift  );  
```  
  
#### Parámetros  
 \[in\] `value`  
 El valor que se va a girar.  
  
 \[in\] `shift`  
 El número de bits que se va a girar.  
  
## Valor devuelto  
 El valor girado.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_rotr8`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotr16`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 A diferencia de una operación de desplazamiento a la derecha, al ejecutar un giro a la derecha, los bits de valor inferior baja que caen fuera del extremo inferior se mueven a las posiciones de los bits de valor superior.  
  
## Ejemplo  
  
```  
// rotr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotr8, _rotr16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,  
                i, _rotr8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x right by %d bits "  
             "gives 0x%x\n",  
            s, nBit, _rotr16(s, nBit));  
}  
```  
  
  **La rotación de 0x41 a la derecha 0 bits da 0x41**  
**La rotación de 0x41 a la derecha 1 bit da 0xa0**  
**La rotación de 0x41 a la derecha 2 bits da 0x50**  
**La rotación de 0x41 a la derecha 3 bits da 0x28**  
**La rotación de 0x41 a la derecha 4 bits da 0x14**  
**La rotación de 0x41 a la derecha 5 bits da 0xa**  
**La rotación de 0x41 a la derecha 6 bits da 0x5**  
**La rotación de 0x41 a la derecha 7 bits da 0x82**  
**La rotación de 0x12 corto sin signo a la derecha 10 bits da 0x480**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_rotl8, \_rotl16](../intrinsics/rotl8-rotl16.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)