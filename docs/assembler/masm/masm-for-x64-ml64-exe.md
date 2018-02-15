---
title: MASM para x64 (ml64.exe) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a42b25b5d86d181bed907a3b437d28f3cbf5e820
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="masm-for-x64-ml64exe"></a>MASM para x64 (ml64.exe)

Visual Studio incluye versiones de 32 y 64 bits hospedadas de MASM para código de destino x64. Denominado ml64.exe, trata el ensamblador que acepta x64 lenguaje ensamblador. Cuando se elige una carga de trabajo de C++ durante la instalación de Visual Studio, se instalan las herramientas de línea de comandos de MASM. Estas herramientas no están disponibles como descarga independiente. Para descargar e instalar una copia de Visual Studio, vea [https://www.visualstudio.com/](https://www.visualstudio.com/). Si no desea instalar el IDE de Visual Studio, pero sólo desea que las herramientas de línea de comandos, consulte el **Build Tools para Visual Studio de 2017** opción el [descargas de Visual Studio](https://www.visualstudio.com/downloads/) página.

Utilizar MASM para generar código para x64 tiene como destino en la línea de comandos, debe utilizar un símbolo del sistema para desarrolladores para x64 destinos, que establece la ruta de acceso necesaria y otras variables de entorno. Para obtener información sobre cómo iniciar un símbolo del sistema para desarrolladores, consulte [de compilación de C/C ++ en la línea de comandos](../../build/building-on-the-command-line.md).

Para obtener información sobre las opciones de línea de comandos ml64.exe, consulte [ML y ML64 Command-Line Reference](../../assembler/masm/ml-and-ml64-command-line-reference.md).  
  
Ensamblador alineado o el uso de la palabra clave ASM no se admite para x64 o destinos ARM. Migrar su x86 código ese ensamblador alineado de usos x64 o ARM, puede convertir el código de C++, usar funciones intrínsecas del compilador o crear archivos de código fuente de lenguaje ensamblador. El compilador de Visual C++ admite funciones intrínsecas para que pueda utilizar las instrucciones de una función especial, para bits de ejemplo, con privilegios, análisis y pruebas, interbloqueos y así sucesivamente, en como cerca de una manera multiplataforma como sea posible. Para obtener información sobre funciones intrínsecas disponibles, consulte [funciones intrínsecas del compilador](../../intrinsics/compiler-intrinsics.md).  

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Agregar un archivo de lenguaje ensamblador a un proyecto de Visual C++  
  
El sistema de proyectos de Visual Studio es compatible con archivos de lenguaje ensamblador generados mediante el uso de MASM en los proyectos de C++. Puede crear x64 archivos de código en lenguaje ensamblador y compilarlas en archivos de objeto mediante MASM, que admite totalmente x64. A continuación, puede vincular estos archivos de objeto en el código de C++ creado para x64 destinos. Se trata de una manera de solucionar la falta de un x64 ensamblador alineado.  

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Para agregar un archivo de lenguaje ensamblador a un proyecto existente de Visual C++

1. Seleccione el proyecto en **el Explorador de soluciones**. En la barra de menús, elija **proyecto**, **Build Customizations**.

1. En el **archivos de personalización de compilación de Visual C++** diálogo cuadro, active la casilla de verificación junto a **masm(.targets,.props)**. Elija **Aceptar** para guardar la selección y cerrar el cuadro de diálogo.

1. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**. 

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **archivo C++ (.cpp)** en el panel central. En el **nombre** control de edición, escriba un nuevo nombre de archivo que tiene un **ASM** extensión en lugar de .cpp. Elija **agregar** para agregar el archivo al proyecto y cerrar el cuadro de diálogo.

Crear el código de lenguaje ensamblador en el archivo de ASM agregado. Cuando se compila una solución, se invoca el ensamblador MASM para montar el archivo de ASM en un archivo de objeto que está vinculado, a continuación, en el proyecto. Para facilitar el acceso de símbolos, declare las funciones de ensamblador como `extern "C"` en el código fuente de C++, en lugar de usar C++ nombre convenciones de decoración en su lenguaje de ensamblador de archivos de código fuente.
  
## <a name="ml64-specific-directives"></a>Directivas específicas de ml64  

Puede usar las siguientes directivas de ml64 específica en el código fuente de lenguaje ensamblador que tenga como destino x64:  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
Además, el [PROC](../../assembler/masm/proc.md) directiva se ha actualizado para su uso con ml64.exe.  
  
## <a name="32-bit-address-mode-address-size-override"></a>Modo de direccionamiento de 32 bits (reemplazo de tamaño de dirección)  

MASM emite la invalidación de tamaño de la dirección de 0x67 si un operando de memoria incluye registros de 32 bits. Por ejemplo, en los ejemplos siguientes pueden causar la invalidación de tamaño de la dirección que se emitan:  
  
```MASM  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
MASM se da por supuesto que si un desplazamiento de 32 bits aparece solo como un operando de memoria, direccionamiento de 64 bits está diseñado. Actualmente no hay ninguna compatibilidad para el direccionamiento de 32 bits con operandos de este tipo.  
  
Por último, la combinación de tamaños de registro en un operando de memoria, como se muestra en el siguiente código genera un error.  
  
```MASM  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## <a name="see-also"></a>Vea también  

[Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)