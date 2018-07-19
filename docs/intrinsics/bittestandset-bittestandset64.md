---
title: _bittestandset, _bittestandset64 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _bittestandset_cpp
- _bittestandset64_cpp
- _bittestandset64
- _bittestandset
dev_langs:
- C++
helpviewer_keywords:
- bts instruction
- _bittestandset intrinsic
- _bittestandset64 intrinsic
ms.assetid: 6d6c8670-fea0-4c1c-9aad-2bb842715203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928391912d325faaf2e70a27519fdf969539fbca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337644"
---
# <a name="bittestandset-bittestandset64"></a>_bittestandset, _bittestandset64
**Específicos de Microsoft**  
  
 Generar una instrucción que examina el bit `b` de la dirección `a`, devuelve su valor actual y establece el bit en 1.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char _bittestandset(  
   long *a,  
   long b  
);  
unsigned char _bittestandset64(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in, out] `a`  
 Puntero a la memoria que se va a examinar.  
  
 [in] `b`  
 La posición de bit que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 El bit en la posición especificada.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_bittestandset`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_bittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
Flags: 0x2  
Flags: 0x6  
Flags: 0xe  
Flags: 0x6  
Flags: 0x4  
Flags: 0x0  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)