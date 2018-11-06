---
title: MASM para x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 0404bff54a08988a72fcb0a0c075a4446bf90f48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596227"
---
# <a name="masm-for-x64-ml64exe"></a>MASM para x64 (ml64.exe)

Visual Studio incluye 32 bits y 64 bits versiones hospedadas de Microsoft Assembler (MASM) al código de destino x64. Denominado ml64.exe, trata el ensamblador que acepta x64 lenguaje ensamblador. Cuando se elige una carga de trabajo de C++ durante la instalación de Visual Studio, se instalan las herramientas de línea de comandos de MASM. Las herramientas MASM no están disponibles como descarga independiente. Para obtener instrucciones sobre cómo descargar e instalar una copia de Visual Studio, consulte [instalar Visual Studio](/visualstudio/install/install-visual-studio). Si no desea instalar el IDE de Visual Studio completa, pero sólo desea que las herramientas de línea de comandos, descargue el [Build Tools para Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Utilizar MASM para generar código para x64 tiene como destino en la línea de comandos, debe usar un símbolo del sistema para desarrolladores para x64 destinos, que establece la ruta de acceso necesario y otras variables de entorno. Para obtener información sobre cómo iniciar un símbolo del sistema para desarrolladores, consulte [código de C o C++ de compilación en la línea de comandos](../../build/building-on-the-command-line.md).

Para obtener información sobre las opciones de línea de comandos ml64.exe, consulte [ML y ML64 referencia de línea de comandos](../../assembler/masm/ml-and-ml64-command-line-reference.md).

Ensamblador alineado o el uso de la palabra clave ASM no se admite para x64 o destinos ARM. Portar su x86 código ese ensamblador alineado de usos x64 o ARM, puede convertir el código de c++, usar funciones intrínsecas del compilador o crear el lenguaje de ensamblador de archivos de origen. El compilador de Visual C++ admite las funciones intrínsecas para que le permiten usar instrucciones funciones especiales, por ejemplo, con privilegios, bit análisis y pruebas, interbloqueos y así sucesivamente, en como cerca de una manera multiplataforma como sea posible. Para obtener información sobre funciones intrínsecas disponibles, consulte [intrínsecos del compilador](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Agregar un archivo de lenguaje de ensamblador a un proyecto de Visual C++

El sistema del proyecto de Visual Studio es compatible con los archivos de lenguaje ensamblador generados mediante el uso de MASM en los proyectos de C++. Puede crear x64 origen del lenguaje ensamblador de archivos y compilarlos en archivos objeto mediante el uso de MASM, que es compatible con x64 totalmente. A continuación, puede vincular estos archivos de objeto en el código de C++ compilado para x64 destinos. Se trata de una forma de solucionar la falta de un x64 ensamblador alineado.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Para agregar un archivo de lenguaje ensamblador a un proyecto existente de Visual C++

1. Seleccione el proyecto en el **Explorador de soluciones**. En la barra de menús, elija **proyecto**, **personalizaciones de compilación**.

1. En el **archivos de personalización de compilación de Visual C++** diálogo cuadro, active la casilla de verificación situada junto a **masm(.targets,.props)**. Elija **Aceptar** para guardar la selección y cerrar el cuadro de diálogo.

1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **archivo C++ (.cpp)** en el panel central. En el **nombre** control de edición, escriba un nuevo nombre de archivo que tiene un **.asm** extensión en lugar de cpp. Elija **agregar** para agregar el archivo al proyecto y cerrar el cuadro de diálogo.

Crear el código de lenguaje ensamblador en el archivo .asm agregado. Cuando se compila la solución, se invoca el ensamblador MASM para ensamblar el archivo .asm en un archivo de objeto que esté vinculado a continuación, en el proyecto. Para facilitar el acceso de símbolos, declare las funciones de ensamblador como `extern "C"` en el código fuente de C++, en lugar de usar C++ nombre convenciones de decoración en su lenguaje de ensamblador de archivos de código fuente.

## <a name="ml64-specific-directives"></a>Directivas específicas de ml64

Puede usar las siguientes directivas de ml64 específica en el código fuente de lenguaje ensamblador que tenga como destino x64:

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

Además, el [PROC](../../assembler/masm/proc.md) directiva se ha actualizado para su uso con ml64.exe.

## <a name="32-bit-address-mode-address-size-override"></a>Modo de direccionamiento de 32 bits (reemplazo de tamaño de dirección)

MASM emite la invalidación de tamaño de dirección 0x67 si un operando de memoria incluye registros de 32 bits. Por ejemplo, los ejemplos siguientes producen el reemplazo de tamaño de dirección que se emitan:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM se da por supuesto que si un desplazamiento de 32 bits aparece solo como un operando de memoria, direccionamiento de 64 bits está diseñado. Actualmente no hay ninguna compatibilidad para el direccionamiento de 32 bits con operandos de este tipo.

Por último, al mezclar los tamaños de registro dentro de un operando de memoria, como se muestra en el código siguiente, genera un error.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Vea también

[Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>