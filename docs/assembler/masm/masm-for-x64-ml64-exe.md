---
title: MASM para x64 (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 5e324414a0d4d7e74bb28d54c1d858ef6fb9793c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312747"
---
# <a name="masm-for-x64-ml64exe"></a>MASM para x64 (ml64.exe)

Visual Studio incluye versiones hospedadas de 32 bits y de 64 bits de Microsoft Assembler (MASM) para tener como destino código x64. Con el nombre ml64. exe, es el ensamblador que acepta el lenguaje de ensamblador x64. Las herramientas de línea de comandos de MASM se instalan al C++ elegir una carga de trabajo durante la instalación de Visual Studio. Las herramientas de MASM no están disponibles como descarga independiente. Para obtener instrucciones sobre cómo descargar e instalar una copia de Visual Studio, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio). Si no desea instalar el IDE completo de Visual Studio, pero solo desea las herramientas de línea de comandos, descargue las [herramientas de compilación para Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Para usar MASM para compilar código para destinos x64 en la línea de comandos, debe usar un símbolo del sistema para desarrolladores de destinos x64, que establece la ruta de acceso necesaria y otras variables de entorno. Para obtener información sobre cómo iniciar un símbolo del sistema para desarrolladores, vea [compilar C/C++ Code en la línea de comandos](../../build/building-on-the-command-line.md).

Para obtener información sobre las opciones de línea de comandos de ml64. exe, consulte [la referencia de línea de comandos de ml y ml64](ml-and-ml64-command-line-reference.md).

No se admite el ensamblador alineado ni el uso de la palabra clave ASM para destinos x64 o ARM. Para migrar el código x86 que usa el ensamblador en línea a x64 o ARM, puede convertir el código C++en, usar funciones intrínsecas del compilador o crear archivos de código fuente del lenguaje ensamblador. El compilador de Microsoft C++ admite intrínsecos para permitirle usar instrucciones de funciones especiales, por ejemplo, privileged, SCAN/test, entrelazada, etc., de la forma más cercana posible a la plataforma. Para obtener información sobre los intrínsecos disponibles, vea [intrínsecos del compilador](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Agregar un archivo de lenguaje de ensamblador a un proyecto C++ de Visual Studio

El sistema de proyectos de Visual Studio admite archivos de lenguaje de ensamblado compilados C++ mediante MASM en sus proyectos. Puede crear archivos de origen de lenguaje ensamblador x64 y compilarlos en archivos de objeto mediante MASM, que admite completamente x64. Después, puede vincular estos archivos objeto al C++ código compilado para destinos x64. Se trata de una manera de solucionar la falta de un ensamblador alineado x64.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Para agregar un archivo de lenguaje de ensamblador a un proyecto de C++ Visual Studio existente

1. Seleccione el proyecto en el **Explorador de soluciones**. En la barra de menús, elija **proyecto**y **personalizaciones de compilación**.

1. En el cuadro de diálogo **archivos de personalización de compilación C++ visual** , active la casilla junto a **MASM (. targets,. props)** . Elija **Aceptar** para guardar la selección y cerrar el cuadro de diálogo.

1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione  **C++ archivo (. cpp)** en el panel central. En el control de edición **nombre** , escriba un nuevo nombre de archivo que tenga una extensión **. asm** en lugar de. cpp. Elija **Agregar** para agregar el archivo al proyecto y cerrar el cuadro de diálogo.

Cree el código del lenguaje de ensamblador en el archivo. asm que ha agregado. Al compilar la solución, se invoca el ensamblador de MASM para ensamblar el archivo. asm en un archivo objeto que, a continuación, se vincula en el proyecto. Para facilitar el acceso a los símbolos, declare las funciones de ensamblador C++ como `extern "C"` en el código fuente, C++ en lugar de usar las convenciones de decoración de nombres en los archivos de origen del lenguaje de ensamblado.

## <a name="ml64-specific-directives"></a>Directivas específicas de ml64

Puede usar las siguientes directivas específicas de ml64 en el código fuente del lenguaje de ensamblador que tiene como destino x64:

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

Además, la directiva [proc](proc.md) se ha actualizado para su uso con ml64. exe.

## <a name="32-bit-address-mode-address-size-override"></a>Modo de dirección de 32 bits (invalidación de tamaño de dirección)

MASM emite la invalidación de tamaño de dirección 0x67 si un operando de memoria incluye registros de 32 bits. Por ejemplo, los ejemplos siguientes hacen que se emita la invalidación del tamaño de dirección:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM supone que si un desplazamiento de 32 bits aparece solo como un operando de memoria, el direccionamiento de 64 bits está previsto. Actualmente no se admite el direccionamiento de 32 bits con tales operandos.

Por último, al mezclar los tamaños de registro dentro de un operando de memoria, como se muestra en el código siguiente, se genera un error.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Vea también

[Referencia de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)
