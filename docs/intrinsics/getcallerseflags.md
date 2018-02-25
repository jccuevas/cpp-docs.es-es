---
title: __getcallerseflags | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _getcallerseflags
- _getcallerseflags_cpp
dev_langs:
- C++
helpviewer_keywords:
- _getcallerseflags intrinsic
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f90d7627267be551b2d3060e6b1b6315e08644cf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="getcallerseflags"></a>__getcallerseflags
**Específicos de Microsoft**  
  
 Devuelve el valor EFLAGS desde el contexto del llamador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned int __getcallerseflags(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Valor EFLAGS desde el contexto del llamador.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__getcallerseflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
```  
// getcallerseflags.cpp  
// processor: x86, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__getcallerseflags)  
  
unsigned int g()  
{  
    unsigned int EFLAGS = __getcallerseflags();  
    printf_s("EFLAGS 0x%x\n", EFLAGS);  
    return EFLAGS;  
}  
unsigned int f()  
{  
    return g();  
}  
  
int main()  
{  
    unsigned int i;  
    i = f();  
    i = g();  
    return 0;  
}  
```  
  
```Output  
EFLAGS 0x202  
EFLAGS 0x206  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)