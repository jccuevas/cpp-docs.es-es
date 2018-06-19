---
title: __debugbreak | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3dcead3129c87b2d02f8822019af763c0fe8b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340182"
---
# <a name="debugbreak"></a>__debugbreak
**Específicos de Microsoft**  
  
 Produce un punto de interrupción en el código, donde se pedirá al usuario que ejecute el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|---------------|------------------|------------|  
|`__debugbreak`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<INTRIN.h >|  
  
## <a name="remarks"></a>Comentarios  
 El `__debugbreak` compilador intrínseco, de forma similar a [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), es una manera portable de Win32 para hacer que un punto de interrupción.  
  
> [!NOTE]
>  Cuando se compila con **/CLR**, una función que contiene `__debugbreak` se compila en MSIL. `asm int 3` produce una función que se va a compilar en código nativo. Para obtener más información, consulte [__asm](../assembler/inline/asm.md).  
  
 Por ejemplo:  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 es similar a:  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 en un equipo x86.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)