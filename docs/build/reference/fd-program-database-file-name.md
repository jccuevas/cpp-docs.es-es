---
title: /Fd (Nombre del archivo de base de datos del programa)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292736"
---
# <a name="fd-program-database-file-name"></a>/Fd (Nombre del archivo de base de datos del programa)

Especifica un nombre de archivo para el archivo de base de datos (PDB) de programa creado por [/Z7, / Zi, /ZI (formato de la información de depuración)](z7-zi-zi-debug-information-format.md).

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

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

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
