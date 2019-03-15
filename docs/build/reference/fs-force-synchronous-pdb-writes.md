---
title: /FS (forzar escrituras de PDB sincrónicas)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 97ffb9529087329cf327ba704523b93d5d9b99b1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817600"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (forzar escrituras de PDB sincrónicas)

Fuerza que las escrituras en el archivo de programa (PDB) de la base de datos, creado por [/Zi](z7-zi-zi-debug-information-format.md) o [/Zi](z7-zi-zi-debug-information-format.md)— se serialicen mediante MSPDBSRV. EXE.

## <a name="syntax"></a>Sintaxis

```
/FS
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando **/Zi** o **/Zi** se especifica, el compilador bloquea los archivos PDB para escribir información de tipo y la información de depuración simbólica. Esto puede reducir significativamente el tiempo que tarda el compilador en generar la información de tipos cuando hay muchos tipos. Si otro proceso bloquea temporalmente el archivo PDB (por ejemplo, un programa antivirus), las escrituras del compilador pueden producir errores y puede aparecer un error irrecuperable. Este problema también puede ocurrir cuando varias copias de cl.exe tienen acceso al mismo archivo PDB, por ejemplo, si la solución tiene proyectos independientes que utilizan los mismos directorios intermedios o si están habilitados los directorios de salida y las compilaciones en paralelo. El **/FS** opción del compilador impide que el compilador bloquee el archivo PDB y fuerza las escrituras a recorrer MSPDBSRV. EXE, que serializa el acceso. Esto puede prolongar las compilaciones y no evita todos los errores que pueden aparecer cuando varias instancias de cl.exe tienen acceso al archivo PDB al mismo tiempo. Recomendamos cambiar la solución de forma que los proyectos independientes escriban en ubicaciones intermedias y de salida separadas, o de forma que uno de los proyectos dependa del otro para forzar las compilaciones de proyecto serializadas.

El [/MP](mp-build-with-multiple-processes.md) opción habilita **/FS** de forma predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir `/FS` y, a continuación, elija **Aceptar**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
