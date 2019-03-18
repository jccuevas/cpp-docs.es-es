---
title: /VERBOSE (Mostrar mensajes de progreso)
ms.date: 11/04/2016
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: 7aed1e17034b40ffdad4da4136fc5a64361b3d77
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809150"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Mostrar mensajes de progreso)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Comentarios

El vinculador envía información sobre el progreso de la sesión de vinculación a la **salida** ventana. En la línea de comandos, la información se envía a la salida estándar y puede redirigirse a un archivo.

|Opción|Descripción|
|------------|-----------------|
|/VERBOSE|Muestra detalles sobre el proceso de vinculación.|
|/VERBOSE:ICF|Mostrar información acerca de la actividad del vinculador que resulta del uso de [/OPT: ICF](opt-optimizations.md).|
|/VERBOSE:INCR|Muestra información sobre el proceso de vinculación incremental.|
|/VERBOSE:LIB|Muestra mensajes de progreso que indican solamente las bibliotecas de búsqueda.<br /><br /> La información presentada incluye el proceso de búsqueda en las bibliotecas y enumera los nombres de las bibliotecas y objetos (con la ruta de acceso completa), el símbolo que se esté resolviendo de cada biblioteca y una lista de los objetos que hacen referencia al símbolo.|
|/VERBOSE:REF|Muestra información acerca de la actividad del vinculador que resulta del uso de [/OPT: ref](opt-optimizations.md).|
|/VERBOSE:SAFESEH|Muestra información acerca de los módulos que no son compatibles con cuando control de excepciones seguro [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) no se especifica.|
|/VERBOSE:UNUSEDLIBS|Muestra información sobre los archivos de biblioteca que no se usan cuando se crea la imagen.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el **vinculador** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Agregue la opción de la **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
