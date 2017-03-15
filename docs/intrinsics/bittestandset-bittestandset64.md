---
title: "_bittestandset, _bittestandset64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_bittestandset_cpp"
  - "_bittestandset64_cpp"
  - "_bittestandset64"
  - "_bittestandset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bittestandset intrinsic"
  - "_bittestandset64 intrinsic"
  - "bts instruction"
ms.assetid: 6d6c8670-fea0-4c1c-9aad-2bb842715203
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _bittestandset, _bittestandset64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Generar una instrucción que examina el bit `b` de la dirección `a`, devuelve su valor actual y establece el bit en 1.  
  
## Sintaxis  
  
```  
unsigned char _bittestandset(    long *a,    long b ); unsigned char _bittestandset64(    __int64 *a,    __int64 b );  
```  
  
#### Parámetros  
 \[in, out\] `a`  
 Puntero a la memoria que se va a examinar.  
  
 \[in\] `b`  
 La posición de bit que se va a para probar.  
  
## Valor devuelto  
 El bit en la posición especificada.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_bittestandset`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_bittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## Ejemplo  
  
```  
// bittestandset.cpp  
// processor: x86, ARM, x64  
// This example uses several of the _bittest family of intrinsics  
// to implement a Flags class that allows bit level access to an  
// integer field.  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_bittestandset, _bittestandreset,\  
                  _bittestandcomplement, _bittest)  
  
class Flags  
{  
private:  
    long flags;  
    long* oldValues;  
  
public:  
    Flags() : flags(0)  
    {  
        oldValues = new long[32];  
    }  
  
    ~Flags()  
    {  
        delete oldValues;  
    }  
  
    void SetFlagBit(long nBit)  
    {  
        // We omit range checks on the argument  
        oldValues[nBit] = _bittestandset(&flags, nBit);  
        printf_s("Flags: 0x%x\n", flags);  
    }  
    void ClearFlagBit(long nBit)  
    {  
        oldValues[nBit] = _bittestandreset(&flags, nBit);  
        printf_s("Flags: 0x%x\n", flags);  
    }  
    unsigned char GetFlagBit(long nBit)  
    {  
        unsigned char result = _bittest(&flags, nBit);  
        printf_s("Flags: 0x%x\n", flags);  
        return result;  
    }  
    void RestoreFlagBit(long nBit)  
    {  
        if (oldValues[nBit])  
            oldValues[nBit] = _bittestandset(&flags, nBit);  
        else  
            oldValues[nBit] = _bittestandreset(&flags, nBit);  
        printf_s("Flags: 0x%x\n", flags);       
    }  
    unsigned char ToggleBit(long nBit)  
    {  
        unsigned char result = _bittestandcomplement(&flags, nBit);  
        printf_s("Flags: 0x%x\n", flags);  
        return result;  
    }  
};  
  
int main()  
{  
    Flags f;  
    f.SetFlagBit(1);  
    f.SetFlagBit(2);  
    f.SetFlagBit(3);  
    f.ClearFlagBit(3);  
    f.ToggleBit(1);  
    f.RestoreFlagBit(2);  
}  
```  
  
  **Indicadores: 0x2**  
**Indicadores: 0x6**  
**Indicadores: 0xe**  
**Indicadores: 0x6**  
**Indicadores: 0x4**  
**Indicadores: 0x0**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)