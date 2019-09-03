---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217924"
---
# <a name="__debugbreak"></a>__debugbreak

**Específicos de Microsoft**

Produce un punto de interrupción en el código, donde se pedirá al usuario que ejecute el depurador.

## <a name="syntax"></a>Sintaxis

```C
void __debugbreak();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Encabezado|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Comentarios

La `__debugbreak` función intrínseca del compilador, similar a [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak), es una forma portable de Win32 de producir un punto de interrupción.

> [!NOTE]
> Al compilar con **/CLR**, una `__debugbreak` función que contiene se compilará en MSIL. `asm int 3` produce una función que se va a compilar en código nativo. Para obtener más información, vea _ _ [ASM](../assembler/inline/asm.md).

Por ejemplo:

```C
main() {
   __debugbreak();
}
```

es similar a:

```C
main() {
   __asm {
      int 3
   }
}
```

en un equipo x86.

En ARM64, el `__debugbreak` intrínseco se compila en la instrucción `brk #0xF000`.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
