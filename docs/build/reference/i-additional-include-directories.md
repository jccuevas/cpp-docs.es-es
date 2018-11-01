---
title: /I (directorios de inclusión adicionales)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 0dc1769924880d8cb1b5dc173dd614e87584cac9
ms.sourcegitcommit: 45835842604602a011813d0cd70abc5df91b89ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750397"
---
# <a name="i-additional-include-directories"></a>/I (directorios de inclusión adicionales)

Agrega un directorio a la lista de directorios para buscar archivos de inclusión.

## <a name="syntax"></a>Sintaxis

> **/I**[]*directorio*

### <a name="arguments"></a>Argumentos

*Directorio*<br/>
Busca en el directorio para agregarse a la lista de directorios para archivos de inclusión.

## <a name="remarks"></a>Comentarios

Para agregar más de un directorio, use esta opción varias veces. Los directorios se buscan solo hasta que se encuentra el archivo de inclusión especificado.

Puede usar esta opción con el ([/X (omitir estándar incluyen rutas de acceso)](../../build/reference/x-ignore-standard-include-paths.md)) opción.

El compilador busca en los directorios en el orden siguiente:

1. Si se especifica mediante un [#include (directiva)](../../preprocessor/hash-include-directive-c-cpp.md) en forma de comillas dobles, busca primero en directorios locales. La búsqueda comienza en el mismo directorio que el archivo que contiene el **#include** instrucción. Si se produce un error buscar el archivo, busca en los directorios de abiertas actualmente los archivos de inclusión, en el orden inverso en el que se abrieron. La búsqueda comienza en el directorio del archivo de inclusión principal y continúa hacia arriba por los directorios de cualquier archivo de inclusión primario principal.

1. Si se especifica mediante un **#include** directiva en ángulo formulario corchete angular de cierre, o si la búsqueda de directorio local ha fallado, busca en los directorios especificados mediante el uso de la **/I** opción, en el orden en que CL encuentra en la línea de comandos.

1. Los directorios especificados en el **INCLUDE** variable de entorno.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **General** página de propiedades.

1. Modificar el **directorios de inclusión adicionales** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Ejemplo

El siguiente comando busca los archivos de inclusión solicitados por MAIN.c en el orden siguiente: en primer lugar, si se especifica mediante el uso de comillas dobles, se buscan en archivos locales. A continuación, la búsqueda continúa en el directorio \INCLUDE, a continuación, en el directorio \MY\INCLUDE y, por último, en los directorios asignados a la variable de entorno INCLUDE.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)