---
title: /c (Compilar sin vincular)
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: cdce86f9ba74b2541529d922c580d6393a93f775
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416467"
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
