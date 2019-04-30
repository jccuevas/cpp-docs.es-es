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
ms.openlocfilehash: a5eb6a10f3c4833ecc3e9d9c8451894788ebd938
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292320"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (optimizar código para una aplicación para Windows)

Tiene como resultado un código más eficaz para un archivo .exe para tener acceso a las variables de almacenamiento local de subprocesos (TLS).

## <a name="syntax"></a>Sintaxis

```
/GA
```

## <a name="remarks"></a>Comentarios

**/GA** declarado acelera el acceso a datos con [__declspec (Thread)](../../cpp/declspec.md) en un programa basado en Windows. Cuando se establece esta opción, el [__tls_index](/windows/desktop/ProcThread/thread-local-storage) macro se supone que es 0.

Uso de **/GA** para puede dar lugar a un archivo DLL de generación de código incorrecto.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
