---
title: /JMC (Depuración de Solo mi código)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 90fcad40b3322f8a8ae7ffc58875c2850f143138
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341012"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (Depuración de Solo mi código)

Especifica la compatibilidad del compilador con la depuración de *solo mi código* nativa en el depurador de Visual Studio. Esta opción admite la configuración de usuario que permite que Visual Studio depure paso a paso por instrucciones el sistema, el marco de trabajo, la biblioteca y otras llamadas que no son de usuario, así como contraer esas llamadas en la ventana pila de llamadas. La opción del compilador **/JMC** está disponible a partir de Visual Studio 2017, versión 15,8.

## <a name="syntax"></a>Sintaxis

> **/JMC**\[ **-** ]

## <a name="remarks"></a>Comentarios

La configuración de [solo mi código](/visualstudio/debugger/just-my-code) de Visual Studio especifica si el depurador de Visual Studio realiza un paso más en el sistema, el marco, la biblioteca y otras llamadas que no son de usuario. La opción del compilador **/JMC** habilita la compatibilidad con la depuración de solo mi código en el código nativo C++ . Cuando **/JMC** está habilitado, el compilador inserta llamadas a una función auxiliar `__CheckForDebuggerJustMyCode`,, en el prólogo de la función. La función auxiliar proporciona enlaces que admiten operaciones de Solo mi código paso en el depurador de Visual Studio. Para habilitar solo mi código en el depurador de Visual Studio, en la barra de menús, elija **herramientas** > **Opciones**y, a continuación  > , establezca la opción en depuración**General** > **Habilitar solo mi código**.

La opción **/JMC** requiere que el código se vincule a la biblioteca en tiempo de ejecución de C (CRT `__CheckForDebuggerJustMyCode` ), que proporciona la función auxiliar. Si el proyecto no se vincula a CRT, es posible que vea el error del vinculador **LNK2019: símbolo externo sin resolver __CheckForDebuggerJustMyCode**. Para resolver este error, vincule a CRT o deshabilite la opción **/JMC** .

De forma predeterminada, la opción del compilador **/JMC** está desactivada. Sin embargo, a partir de Visual Studio 2017 versión 15,8, esta opción está habilitada en la mayoría de las plantillas de proyecto de Visual Studio. Para deshabilitar explícitamente esta opción, utilice la opción **/JMC-** en la línea de comandos. En Visual Studio, abra el cuadro de diálogo páginas de propiedades del proyecto y cambie la propiedad **compatibilidad solo mi código** depuración en la página de **propiedades** >  > **C++C/** **General** de propiedades de configuración a **No**.

Para obtener más información, vea [ C++ solo mi código](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) en [especificar si se va a depurar solo el código de usuario mediante solo mi código en Visual Studio](/visualstudio/debugger/just-my-code)y la entrada del blog del equipo visual C++ que [anuncia C++ solo mi código paso a paso en Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la  > página de propiedades**CC++/**  > **General** de propiedades de configuración.

1. Modifique la propiedad Solo mi código de depuración de **compatibilidad** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
