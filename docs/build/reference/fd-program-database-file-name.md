---
title: -Fd (nombre de archivo de base de datos de programa) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfa59f889c472651eb40ddcf297ca51bd34f4e41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389946"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nombre del archivo de base de datos del programa)

Especifica un nombre de archivo para el archivo de base de datos (PDB) de programa creado por [/Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).

## <a name="syntax"></a>Sintaxis

```
/Fdpathname
```

## <a name="remarks"></a>Comentarios

Sin **/Fd**, el valor predeterminado es el nombre del archivo PDB a los VC*x*0.pdb, donde *x* es la versión principal de Visual C++ en uso.

Si especifica un nombre de ruta de acceso que no incluya un nombre de archivo (la ruta de acceso finaliza con una barra diagonal inversa), el compilador crea un archivo .pdb denominado VC*x*0.pdb en el directorio especificado.

Si especifica un nombre de archivo que no incluye una extensión, el compilador usa .pdb como la extensión.

Esta opción también asigna nombre al archivo de estado (.idb) que se usa para la compilación incremental y recompilación mínima.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Archivos de salida** .

1. Modificar el **nombre del archivo de base de datos de programa** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.

## <a name="example"></a>Ejemplo

Esta línea de comandos crea un archivo .pdb denominado PROG.pdb y un archivo .idb denominado PROG.idb:

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)