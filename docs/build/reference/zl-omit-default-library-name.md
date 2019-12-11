---
title: /Zl (Omitir nombres de biblioteca predeterminada)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: 1bcb90dbf071253dc0561845e3bd713dc42d5aef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988555"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omitir nombres de biblioteca predeterminada)

Omite el nombre predeterminado de la biblioteca en tiempo de ejecución de C del archivo. obj. De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el enlazador hacia la biblioteca correcta.

## <a name="syntax"></a>Sintaxis

```
/Zl
```

## <a name="remarks"></a>Notas

Para obtener más información sobre la biblioteca predeterminada, vea [usar la biblioteca en tiempo de ejecución](md-mt-ld-use-run-time-library.md).

Puede usar **/ZL** para compilar archivos. obj que planea colocar en una biblioteca. Aunque si se omite el nombre de la biblioteca solo se guarda una pequeña cantidad de espacio para un único archivo. obj, el espacio total guardado es significativo en una biblioteca que contiene muchos módulos de objetos.

Esta opción es una opción avanzada. Al establecer esta opción, se quita cierta compatibilidad con la biblioteca en tiempo de ejecución de C que puede necesitar la aplicación, lo que produce errores en tiempo de vínculo si la aplicación depende de esta compatibilidad. Si utiliza esta opción, debe proporcionar los componentes necesarios de otra manera.

Use [/NODEFAULTLIB (omitir bibliotecas)](nodefaultlib-ignore-libraries.md). para indicar al enlazador que omita las referencias de biblioteca en todos los archivos. obj.

Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

Al compilar con **/ZL**, se define `_VC_NODEFAULTLIB`.  Por ejemplo:

```cpp
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **avanzadas** .

1. Modifique la propiedad **Omitir nombres de biblioteca predeterminados** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
