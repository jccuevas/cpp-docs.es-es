---
title: __asm | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- __asm
- _asm
- __asm_cpp
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd279a6324aec6eba50c6c3b7ffe846200d45fe1
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161728"
---
# <a name="asm"></a>__asm

**Específicos de Microsoft**

La palabra clave `__asm` invoca el ensamblador alineado y puede aparecer siempre que una instrucción de C o C++ sea válida. No puede aparecer por sí sola. Debe ir seguida de una instrucción de ensamblado, un grupo de instrucciones entre llaves o, como mínimo, un par de llaves vacío. El término "bloque `__asm`" aquí hace referencia a cualquier instrucción o grupo de instrucciones, incluido o no entre llaves.

> [!NOTE]
> La compatibilidad de Visual C++ con la palabra clave `asm` de C++ estándar se limita al hecho de que el compilador no generará un error en la palabra clave. Sin embargo, un bloque `asm` no generará ningún código importante. Use `__asm` en lugar de `asm`.

## <a name="grammar"></a>Gramática

*bloque de ASM*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *instrucción de ensamblado* **;** <sub>participar</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *lista de instrucciones de ensamblado* **}** **;** <sub>participar</sub>

*lista de instrucciones de ensamblado*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de ensamblado* **;** <sub>participar</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de ensamblado* **;** *lista de instrucciones de ensamblado* **;** <sub>participar</sub>

## <a name="remarks"></a>Comentarios

Si se utiliza sin llaves, la palabra clave `__asm` indica que el resto de la línea es una instrucción de lenguaje de ensamblado. Si se utiliza con llaves, indica que cada línea entre las llaves es una instrucción de lenguaje de ensamblado. Por compatibilidad con versiones anteriores, `_asm` es un sinónimo de `__asm`.

Dado que la palabra clave `__asm` es un separador de la instrucción, puede colocar las instrucciones de ensamblado en la misma línea.

Antes de Visual C++ 2005, la instrucción

```cpp
__asm int 3
```

no se ha provocado el código nativo que se genere cuando se compila con **/CLR**; el compilador traducía la instrucción a una instrucción de salto CLR.

`__asm int 3` ahora da lugar a la generación de código nativo para la función. Si desea que una función para provocar un punto de interrupción en el código y si desea que dicha función compile para MSIL, utilice [__debugbreak](../../intrinsics/debugbreak.md).

Para ofrecer compatibilidad con versiones anteriores, **_asm** es un sinónimo de **__asm** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../../build/reference/za-ze-disable-language-extensions.md) se especifica.

## <a name="example"></a>Ejemplo

El fragmento de código siguiente es un bloque `__asm` simple incluido entre llaves:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Como alternativa, puede colocar `__asm` delante de cada instrucción de ensamblado:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Debido a que la palabra clave `__asm` es un separador de la instrucción, también puede colocar las instrucciones de ensamblado en la misma línea.

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Los tres ejemplos generan el mismo código, pero el primer estilo (incluyendo el bloque `__asm` entre llaves) tiene algunas ventajas. Las llaves separan claramente el código de ensamblado del código de C o C++ y evitan la repetición innecesaria de la palabra clave `__asm`. Las llaves también pueden evitar ambigüedades. Si desea colocar una instrucción de C o C++ en la misma línea que un bloque `__asm`, debe incluir el bloque entre llaves. Sin las llaves, el compilador no puede indicar dónde se detiene el código de ensamblado y dónde comienzan las instrucciones de C o C++. Finalmente, como el texto entre llaves tiene el mismo formato que el texto de MASM normal, se puede cortar y pegar fácilmente el texto de los archivos de código fuente de MASM existentes.

A diferencia de las llaves en C y C++, las llaves que incluyen un bloque `__asm` no afectan al ámbito de las variables. También puede anidar los bloques `__asm`; el anidado no afecta al ámbito de las variables.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../../cpp/keywords-cpp.md)<br/>
[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>