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
ms.openlocfilehash: b52c34014402a235e03c45f82dcd1e5c542e4919
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023105"
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
|`__debugbreak`|x86, ARM, x64|\<intrin.h>|

## <a name="remarks"></a>Comentarios

El `__debugbreak` compilador intrínseco, de forma similar a [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), es una manera portable de Win32 para producir un punto de interrupción.

> [!NOTE]
>  Cuando se compila con **/CLR**, una función que contiene `__debugbreak` se compilará en MSIL. `asm int 3` hace que una función que se compilarán en código nativo. Para obtener más información, consulte [__asm](../assembler/inline/asm.md).

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

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)