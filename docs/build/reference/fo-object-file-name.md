---
title: /Fo (Nombre del archivo objeto)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: 19e84cbb1be53c8e1a7ae32b6ea2fc3ceeb2edae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640341"
---
# <a name="fo-object-file-name"></a>/Fo (Nombre del archivo objeto)

Especifica un nombre de archivo objeto (.obj) o un directorio que se utilizará en lugar del predeterminado.

## <a name="syntax"></a>Sintaxis

```
/Fopathname
```

## <a name="remarks"></a>Comentarios

Si no usa esta opción, el archivo de objeto utiliza el nombre base del archivo de código fuente y la extensión de obj. Puede usar cualquier nombre y extensión que desee, pero la convención recomendada consiste en usar. obj.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Archivos de salida** .

1. Modificar el **nombre del archivo objeto** propiedad.  En el entorno de desarrollo, el archivo de objeto debe tener la extensión. obj.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos crea un archivo de objeto denominado THIS.obj en un directorio existente, \OBJECT, en la unidad B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)