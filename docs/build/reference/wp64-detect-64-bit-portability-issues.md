---
title: /Wp64 (Detectar problemas de portabilidad de 64 bits)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: 5a3cdaf85fa4dc05ece54fc630cb69fc93650e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316553"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Detectar problemas de portabilidad de 64 bits)

Esta opción del compilador está obsoleta. En versiones de Visual Studio anteriores a Visual Studio 2013, detecta problemas de portabilidad de 64 bits en tipos que también están marcados con la palabra clave [__w64](../../cpp/w64.md) .

## <a name="syntax"></a>Sintaxis

```
/Wp64
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, en las versiones de Visual Studio anteriores a Visual Studio 2013, el **/Wp64** opción del compilador está desactivada en el compilador de MSVC que compilaciones de 32 bits x86 código, y en el compilador de MSVC que compilaciones de 64 bits, x64 código.

> [!IMPORTANT]
>  La opción del compilador [/Wp64](wp64-detect-64-bit-portability-issues.md) y la palabra clave [__w64](../../cpp/w64.md) está en desuso en Visual Studio 2010 y Visual Studio 2012 y no se admite a partir de Visual Studio 2013. Si convierte un proyecto que usa este modificador, el modificador no se migrará durante la conversión. Para usar esta opción en Visual Studio 2010 o Visual Studio 2012, debe escribir el modificador del compilador en **Opciones adicionales** , en la sección **Línea de comandos** de las propiedades del proyecto. Si usa la opción del compilador **/Wp64** en la línea de comandos, el compilador emite la Advertencia de la línea de comandos D9002. En lugar de usar esta opción y la palabra clave para detectar problemas de portabilidad de 64 bits, use un compilador MSVC que tenga como destino una plataforma de 64 bits y especifique el [/W4](compiler-option-warning-level.md) opción. Para obtener más información, consulte [C++ configurar proyectos para 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md).

Las variables de los tipos siguientes se comprueban en un sistema operativo de 32 bits como si se usaran en un sistema operativo de 64 bits:

- int

- long

- puntero

Si compila regularmente la aplicación mediante el uso de un compilador que genera 64 bits, x64 código, puede deshabilitar **/Wp64** en las compilaciones de 32 bits porque el compilador de 64 bits detectará todos los problemas. Para obtener más información acerca de cómo el sistema operativo de destino Windows 64 bits, consulte [C++ configurar proyectos para 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.

   Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Modifique el cuadro **Opciones adicionales** para incluir **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Configurar los proyectos de C++ de 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md)
