---
title: Definición de bloques __asm como macros de C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: c48298cf802600995dbbf68885896b6feccb807d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167031"
---
# <a name="defining-asm-blocks-as-c-macros"></a>Definición de bloques __asm como macros de C

**Específicos de Microsoft**

Las macros de C proporcionan una forma cómoda de insertar código de ensamblado en el código fuente, pero exigen especial cuidado, ya que una macro se expande en una sola línea lógica. Para crear macros sin problemas, siga estas reglas:

- Incluya el bloque `__asm` entre llaves.

- Coloque la palabra clave `__asm` delante de cada instrucción de ensamblado.

- Utilice comentarios de C de estilo antiguo ( `/* comment */`) en lugar de comentarios de estilo de ensamblado ( `; comment`) o comentarios de C de una sola línea ( `// comment`).

En el ejemplo siguiente se define una macro sencilla a modo de ilustración:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

A primera vista, las tres palabras clave `__asm` parecen superfluas. Sin embargo, son necesarias, ya que la macro se expande en una sola línea:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

La tercera y la cuarta palabras clave `__asm` son necesarias como separadores de la instrucción. Los únicos separadores de instrucción reconocidos en los bloques `__asm` son el carácter de nueva línea y la palabra clave `__asm`. Como un bloque definido como una macro es una línea lógica, debe separar cada instrucción con `__asm`.

Las llaves también son esenciales. Si las omite, las instrucciones de C o C++ situadas en la misma línea a la derecha de la llamada a la macro pueden confundir al compilador. Sin la llave de cierre, el compilador no puede saber dónde se detiene el código de ensamblado, e interpretará las instrucciones de C o C++ detrás del bloque `__asm` como instrucciones de ensamblado.

Comentarios de estilo de ensamblado que comienzan con un punto y coma (**;**) continúan hasta el final de la línea. Esto causa problemas en las macros porque el compilador omite todo lo que aparece detrás del comentario, hasta el final de la línea lógica. Lo mismo ocurre con los comentarios de C o C++ de una sola línea ( `// comment`). Para evitar errores, utilice comentarios de C de estilo antiguo ( `/* comment */`) en los bloques `__asm` definidos como macros.

Un bloque `__asm` escrito como una macro de C puede aceptar argumentos. A diferencia de las macros de C normales, una macro `__asm` no puede devolver un valor. Así que no puede utilizar estas macros en expresiones de C o C++.

Procure no llamar a macros de este tipo de forma indiscriminada. Por ejemplo, la llamada a una macro del lenguaje de ensamblado en una función declarada con la convención `__fastcall` puede producir resultados inesperados. (Consulte [uso y conservación de registros en un ensamblado alineado](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>