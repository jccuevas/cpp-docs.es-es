---
title: /GA (optimizar código para una aplicación para Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: 85efa03a3f3d267580cbb0442839afb18ac6c313
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492867"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (optimizar código para una aplicación para Windows)

Da como resultado un código más eficaz para un archivo. exe para tener acceso a las variables de almacenamiento local de subprocesos (TLS).

## <a name="syntax"></a>Sintaxis

```
/GA
```

## <a name="remarks"></a>Comentarios

**/GA** agiliza el acceso a los datos declarados con [_ _ declspec (subproceso)](../../cpp/declspec.md) en un programa basado en Windows. Cuando se establece esta opción, se supone que la macro [__tls_index](/windows/win32/ProcThread/thread-local-storage) es 0.

El uso de **/GA** para un archivo dll puede producir una generación de código incorrecta.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
