---
title: -c (compilar sin vincular) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de6fe291bde8652b772c7091c1919836f88960fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710351"
---
# <a name="c-compile-without-linking"></a>/c (Compilar sin vincular)

Impide que la llamada automática a LINK.

## <a name="syntax"></a>Sintaxis

```
/c
```

## <a name="remarks"></a>Comentarios

Compilar con **/c** crea sólo los archivos .obj. Debe llamar a vínculo explícitamente con las opciones para realizar la fase de vinculación de la compilación y los archivos adecuados.

Todos los proyectos internos creados en el entorno de desarrollo usan el **/c** opción predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

- Esta opción no está disponible en el entorno de desarrollo.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Para establecer esta opción del compilador mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos crea los archivos objeto FIRST.obj y SECOND.obj. THIRD.obj se omite.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

Para crear un archivo ejecutable, debe invocar LINK:

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)