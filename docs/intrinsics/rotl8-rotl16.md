---
title: "_rotl8, _rotl16 | Microsoft Docs"
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
  - "_rotl8"
  - "_rotl16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rotl16 intrinsic"
  - "_rotl8 intrinsic"
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rotl8, _rotl16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Girar los valores de entrada a la izquierda hacia el bit más significativo \(MSB\) según un número especificado de posiciones de bit.  
  
## Sintaxis  
  
```  
unsigned char _rotl8(     unsigned char value,     unsigned char shift  ); unsigned short _rotl16(     unsigned short value,     unsigned char shift  );  
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
|`_rotl8`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotl16`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 A diferencia de una operación de desplazamiento a la izquierda, al ejecutar un giro a la izquierda, los bits de valor superior que caen fuera del extremo superior se mueven a las posiciones de los bits menos significativos.  
  
## Ejemplo  
  
```  
// rotl.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotl8, _rotl16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,  
               i, _rotl8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",  
            s, nBit, _rotl16(s, nBit));  
}  
```  
  
  **La rotación de 0x41 a la izquierda 0 bits da 0x41**  
**La rotación de 0x41 a la izquierda 1 bit da 0x82**  
**La rotación de 0x41 a la izquierda 2 bits da 0x5**  
**La rotación de 0x41 a la izquierda 3 bits da 0xa**  
**La rotación de 0x41 a la izquierda 4 bits da 0x14**  
**La rotación de 0x41 a la izquierda 5 bits da 0x28**  
**La rotación de 0x41 a la izquierda 6 bits da 0x50**  
**La rotación de 0x41 a la izquierda 7 bits da 0xa0**  
**La rotación de 0x12 corto sin signo a la izquierda 10 bits da 0x4800**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_rotr8, \_rotr16](../intrinsics/rotr8-rotr16.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)