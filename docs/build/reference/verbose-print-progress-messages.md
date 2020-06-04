---
title: /VERBOSE (Mostrar mensajes de progreso)
ms.date: 06/13/2019
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
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141665"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Mostrar mensajes de progreso)

Muestra mensajes de progreso durante el proceso de vinculación.

## <a name="syntax"></a>Sintaxis

> **/VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR**|**LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD**|**UNUSEDLIBS**}\]

## <a name="remarks"></a>Comentarios

El vinculador envía información sobre el progreso de la sesión de vinculación a la **salida** ventana. En la línea de comandos, la información se envía a la salida estándar y puede redirigirse a un archivo.

| Opción | Descripción |
| ------------ | ----------------- |
| /VERBOSE | Muestra detalles sobre el proceso de vinculación. |
| /VERBOSE:CLR | Muestra información acerca de la actividad del vinculador específico a los objetos y metadatos compilados mediante [/CLR](clr-common-language-runtime-compilation.md). |
| /VERBOSE:ICF | Muestra información acerca de la actividad del vinculador que resulta del uso de [/OPT: ICF](opt-optimizations.md). |
| /VERBOSE:INCR | Muestra información sobre el proceso de vinculación incremental. |
| /VERBOSE:LIB | Muestra mensajes de progreso que indican solamente las bibliotecas de búsqueda.<br/> La información mostrada incluye el proceso de búsqueda de biblioteca. Enumera cada nombre de objeto o biblioteca (con la ruta de acceso completa), que se va a resolver el símbolo de la biblioteca y una lista de objetos que hacen referencia al símbolo. |
| /VERBOSE:REF | Muestra información acerca de la actividad del vinculador que resulta del uso de [/OPT: ref](opt-optimizations.md). |
| /VERBOSE:SAFESEH | Muestra información acerca de los módulos que no son compatibles con el control cuando de excepciones estructurado seguro [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) no se especifica. |
| /VERBOSE:UNUSEDDELAYLOAD | Muestra información sobre cualquier retraso las DLL cargadas que no tienen símbolos que se utiliza cuando se crea la imagen. |
| /VERBOSE:UNUSEDLIBS | Muestra información sobre los archivos de biblioteca que no se usan cuando se crea la imagen. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Agregue la opción de la **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
