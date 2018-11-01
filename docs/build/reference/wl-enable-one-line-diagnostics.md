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
ms.openlocfilehash: 2d2f3c1c7bac19fc0e401067f43e78e3770c6304
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428163"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Habilitar diagnósticos de una línea)

Anexa información adicional a un mensaje de advertencia o error.

## <a name="syntax"></a>Sintaxis

```
/WL
```

## <a name="remarks"></a>Comentarios

Mensajes de error y advertencia del compilador de C++ pueden ir seguidos de información adicional que aparece de forma predeterminada, en una nueva línea. Cuando se compila desde la línea de comandos, se puede anexar a la línea de información adicional al mensaje de advertencia o error. Esto puede ser deseable si captura la salida de compilación en un archivo de registro y, a continuación, procesar ese registro para encontrar todos los errores y advertencias. Un punto y coma para separar el error o mensaje de advertencia de la línea adicional.

No todos los mensajes de error y advertencia tienen una línea adicional de información. El código siguiente generará un error que tiene una línea adicional de información; le permitirá probar el efecto cuando se usa **/WL**.

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)