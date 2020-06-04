---
title: /GF (Eliminar cadenas duplicadas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320488"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminar cadenas duplicadas)

Permite al compilador crear una sola copia de cadenas idénticas en la imagen del programa y en la memoria durante la ejecución. Se trata de una optimización denominada *agrupación* de cadenas que puede crear programas más pequeños.

## <a name="syntax"></a>Sintaxis

```
/GF
```

## <a name="remarks"></a>Observaciones

Si utiliza **/GF**, el sistema operativo no intercambia la parte de la cadena de memoria y puede leer las cadenas desde el archivo de imagen.

**/GF** agrupa cadenas como de solo lectura. Si intenta modificar cadenas en **/GF**, se produce un error de aplicación.

La agrupación de cadenas permite que lo que se pretendía como varios punteros a varios búferes sean varios punteros a un único búfer. En el código `s` `t` siguiente y se inicializan con la misma cadena. La agrupación de cadenas hace que apunten a la misma memoria:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> La opción [/ZI,](z7-zi-zi-debug-information-format.md) utilizada para Editar y continuar, establece automáticamente la opción **/GF.**

> [!NOTE]
> La opción del compilador **/GF** crea una sección direccionable para cada cadena única. Y de forma predeterminada, un archivo de objeto puede contener hasta 65.536 secciones direccionables. Si el programa contiene más de 65.536 cadenas, utilice la opción del compilador [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) para crear más secciones.

**/GF** está en vigor cuando se utiliza [/O1](o1-o2-minimize-size-maximize-speed.md) u [/O2.](o1-o2-minimize-size-maximize-speed.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Generación de código.**

1. Modifique la propiedad **Habilitar agrupación de cadenas.**

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
