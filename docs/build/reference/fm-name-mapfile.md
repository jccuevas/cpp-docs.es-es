---
title: /Fm (Asignar nombre al archivo de asignaciones)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: 9f6290d3dfa4aaadfc9247fd8453d378851328a1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418749"
---
# <a name="fm-name-mapfile"></a>/Fm (Asignar nombre al archivo de asignaciones)

Indica al vinculador para generar un archivo de asignaciones que contiene una lista de segmentos en el orden en que aparecen en el correspondiente archivo .exe o DLL.

## <a name="syntax"></a>Sintaxis

```
/Fmpathname
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, el archivo de asignaciones recibe el nombre de base de que el archivo de código fuente de C o C++ correspondiente con un. Extensión de un mapa.

Especificar **/Fm** tiene el mismo efecto que si se hubiera especificado el [/MAP (Generar archivo de asignaciones)](../../build/reference/map-generate-mapfile.md) opción del vinculador.

Si especifica [/c (compilar sin vincular)](../../build/reference/c-compile-without-linking.md) para suprimir la vinculación, **/Fm** no tiene ningún efecto.

Símbolos globales en un archivo de asignaciones normalmente tienen uno o más caracteres de subrayado iniciales porque el compilador agrega un carácter de subrayado inicial a los nombres de variable. Muchos símbolos globales que aparecen en el archivo de asignaciones se usan internamente por el compilador y las bibliotecas estándar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)
