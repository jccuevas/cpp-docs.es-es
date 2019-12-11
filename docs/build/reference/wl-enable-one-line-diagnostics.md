---
title: /WL (Habilitar diagnósticos de una línea)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: b1ded1cd18eb75ed47b76c1353ad82a7fa497ba9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988566"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Habilitar diagnósticos de una línea)

Anexa información adicional a un mensaje de error o de advertencia.

## <a name="syntax"></a>Sintaxis

```
/WL
```

## <a name="remarks"></a>Notas

Los mensajes de error y de C++ ADVERTENCIA del compilador pueden ir seguidos de información adicional que aparece de forma predeterminada en una línea nueva. Al compilar desde la línea de comandos, se puede anexar la línea de información adicional al mensaje de error o de advertencia. Esto podría ser conveniente si captura la salida de la compilación en un archivo de registro y, a continuación, procesa ese registro para buscar todos los errores y advertencias. Un punto y coma separará el mensaje de error o advertencia de la línea adicional.

No todos los mensajes de error y advertencia tienen una línea de información adicional. El código siguiente generará un error que tiene una línea adicional de información; le permitirá probar el efecto cuando use **/WL**.

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
