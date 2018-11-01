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
ms.openlocfilehash: 7504c12584d931b0f39062f393765ad8124fc0dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561565"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminar cadenas duplicadas)

Permite al compilador crear una copia única de cadenas idénticas en la imagen del programa y en la memoria durante la ejecución. Se trata de una optimización denominada *agrupación de cadenas* que puede crear programas más pequeños.

## <a name="syntax"></a>Sintaxis

```
/GF
```

## <a name="remarks"></a>Comentarios

Si usas **/GF**, el sistema operativo no intercambia la parte de la cadena de la memoria y puede leer las cadenas de realizar una copia del archivo de imagen.

**/GF** agrupa las cadenas como de solo lectura. Si intenta modificar las cadenas bajo **/GF**, se produce un error de aplicación.

Agrupación de cadenas permite lo que se pretendía como punteros de varios a varios búferes varios punteros a un único búfer. En el código siguiente, `s` y `t` se inicializan con la misma cadena. Para que apunten a la misma memoria hace que la agrupación de cadenas:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  El [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción, se utiliza para editar y continuar, se establece automáticamente la **/GF** opción.

> [!NOTE]
>  El **/GF** opción del compilador crea una sección direccionable para cada cadena único. Y, de forma predeterminada, un archivo objeto puede contener hasta 65.536 secciones direccionables. Si el programa contiene más de 65.536 cadenas, utilice el [/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) opción del compilador para crear más secciones.

**/GF** cuando [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o **/O2** se utiliza.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **generación de código** página de propiedades.

1. Modificar el **habilitar agrupación de cadenas** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)