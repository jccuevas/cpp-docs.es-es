---
title: /Yd (Incluir información de depuración en un archivo objeto)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: 55bb8197cd15243f65c90d7fbd2724f91fce23b4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414882"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Incluir información de depuración en un archivo objeto)

Ritmo de completa información de depuración en todos los archivos objeto creado a partir de un archivo de encabezado precompilado (.pch) cuando se usa con el [/Yc](../../build/reference/yc-create-precompiled-header-file.md) y [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) opciones. Desusado.

## <a name="syntax"></a>Sintaxis

```
/Yd
```

## <a name="remarks"></a>Comentarios

**/Yd** está en desuso; Visual C++ ahora admite varios objetos de escritura en un archivo .pdb único, use **/Zi** en su lugar. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](../../build/reference/compiler-options-listed-by-category.md).

A menos que necesite distribuir una información de depuración que contiene la biblioteca, utilice la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción lugar **/Z7** y **/Yd**.

Almacenar información de depuración completa en todos los archivos .obj sólo es necesario para distribuir las bibliotecas que contienen información de depuración. Compilación de la que se ralentiza y requiere espacio en disco considerable. Cuando **/Yc** y **/Z7** se usan sin **/Yd**, el compilador almacena la información de depuración comunes en el primer archivo .obj creado a partir del archivo .pch. El compilador no inserta esta información en los archivos .obj creados posteriormente desde el archivo .pch; Inserta las referencias cruzadas a la información. Independientemente de cuántos archivos .obj que use el archivo .pch, solo un archivo .obj contiene la información de depuración comunes.

Aunque este comportamiento predeterminado logra más rápido el tiempo de compilación y reduce la demanda de espacio en disco, es deseable un pequeño cambio requiere volver a generar el archivo .obj que contiene la información de depuración comunes. En este caso, el compilador debe volver a generar todos los archivos .obj que contiene referencias cruzadas al archivo .obj original. Además, si se usa un archivo .pch común por proyectos diferentes, dependencia de referencias cruzadas a un solo archivo .obj es difícil.

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Ejemplos

Suponga que tiene dos archivos base, F.cpp y G.cpp, cada uno con estos **#include** instrucciones:

```
#include "windows.h"
#include "etc.h"
```

El siguiente comando crea el encabezado precompilado ETC.pch y el archivo objeto F.obj archivos:

```
CL /YcETC.H /Z7 F.CPP
```

El archivo objeto F.obj incluye el tipo y la información de símbolos para WINDOWS.h y ETC.h (y otros archivos de encabezado incluyen). Ahora puede usar el encabezado precompilado ETC.pch para compilar el archivo de código fuente G.cpp:

```
CL /YuETC.H /Z7 G.CPP
```

El archivo objeto G.obj no incluye la información de depuración para el encabezado precompilado pero simplemente hace referencia a esa información en el archivo F.obj. Tenga en cuenta que debe vincular con el archivo F.obj.

Si el encabezado precompilado no se compiló con **/Z7**, puede usarlo en posteriores compilaciones con **/Z7**. Sin embargo, la información de depuración se coloca en el archivo de objeto actual y los símbolos locales para las funciones y tipos definidos en el encabezado precompilado no están disponibles para el depurador.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
