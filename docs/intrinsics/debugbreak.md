---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 97932dfe0e187a13b72ae5fe70d761224721c3ff
ms.sourcegitcommit: 1acb6755e11379026a96f63facac4d33f4dc47ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2019
ms.locfileid: "67314252"
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
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Comentarios

El `__debugbreak` compilador intrínseco, de forma similar a [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), es una manera portable de Win32 para producir un punto de interrupción.

> [!NOTE]
>  Cuando se compila con **/CLR**, una función que contiene `__debugbreak` se compilará en MSIL. `asm int 3` produce una función que se va a compilar en código nativo. Para obtener más información, consulte [__asm](../assembler/inline/asm.md).

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

En ARM64, el `__debugbreak` intrínseca se compila en la instrucción `brk #0xF000`.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
