---
title: / JMC (depuración de sólo mi código) | Microsoft Docs
ms.custom: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /JMC
dev_langs:
- C++
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1da60b43bd151a776278b51a5ee8a22de7ef3b4c
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "40242885"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC (depuración de sólo mi código)

Especifica la compatibilidad de compilador para nativo *solo mi código* depuración en el depurador de Visual Studio. Esta opción es compatible con la configuración del usuario que permite que Visual Studio paso a paso a través del sistema, framework, biblioteca y otras llamadas que no son de usuario y para contraer esas llamadas en la ventana Pila de llamadas. El **/JMC** opción del compilador está disponible a partir de Visual Studio 2017 versión 15,8.

## <a name="syntax"></a>Sintaxis

> **/ JMC**\[**-**]

## <a name="remarks"></a>Comentarios

Visual Studio [solo mi código](/visualstudio/debugger/just-my-code) configuración especifica si el depurador de Visual Studio depura paso a paso del sistema, framework, biblioteca y otras llamadas que no son de usuario. El **/JMC** opción del compilador habilita la compatibilidad con la depuración solo mi código en el código C++ nativo. Cuando **/JMC** está habilitada, el compilador inserta las llamadas a una función auxiliar, `__CheckForDebuggerJustMyCode`, en el prólogo de función. La función auxiliar proporciona enlaces que admiten operaciones de paso de solo mi código de depurador de Visual Studio. Para habilitar solo mi código en el depurador de Visual Studio, en la barra de menús, elija **herramientas** > **opciones**y, a continuación, establezca la opción **depuración**  >  **General** > **habilitar solo mi código**.

El **/JMC** opción requiere que el código se vincula a la biblioteca de tiempo de ejecución de C (CRT), que proporciona el `__CheckForDebuggerJustMyCode` función auxiliar. Si el proyecto no se vincula a la biblioteca CRT, puede ver el error del vinculador **LNK2019: sin resolver símbolos externos __CheckForDebuggerJustMyCode**. Para resolver este error, vincular a CRT o deshabilitar la **/JMC** opción.

De forma predeterminada, el **/JMC** opción del compilador está desactivada. Sin embargo, a partir de Visual Studio 2017 versión 15,8 esta opción está habilitada en la mayoría plantillas de proyecto de Visual Studio. Para deshabilitar explícitamente esta opción, utilice el **/JMC-** opción en la línea de comandos. En Visual Studio, abra el cuadro de diálogo páginas de propiedades de proyecto y cambie el **admiten solo mi código de la depuración** propiedad en el **propiedades de configuración** > **C/C++**  >  **General** página de propiedades para **No**.

Para obtener más información, consulte [C++ solo mi código](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) en [especifique si desea depurar el código de usuario sólo con sólo mi código en Visual Studio](/visualstudio/debugger/just-my-code)y la publicación del blog del equipo de Visual C++ [anuncio de C++ solo mi código Ejecución paso a paso en Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **General** página de propiedades.

1. Modificar el **admiten solo mi código de la depuración** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
