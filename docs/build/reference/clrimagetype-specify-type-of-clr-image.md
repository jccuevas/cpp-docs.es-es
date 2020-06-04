---
title: /CLRIMAGETYPE (Especificar tipo de imagen CLR)
ms.date: 05/16/2019
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: ee2e2ce359a4b877551adf9af71e0187b42cfd42
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837490"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Especificar tipo de imagen CLR)

Establezca el tipo de imagen CLR de la imagen vinculada.

## <a name="syntax"></a>Sintaxis

> **/CLRIMAGETYPE:** {**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Comentarios

El enlazador acepta los objetos nativos y también los objetos de MSIL que se compilan mediante [/clr](clr-common-language-runtime-compilation.md). Las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores. Cuando se pasan objetos mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada. Por ejemplo, si pasa una imagen nativa y una imagen de modo mixto (compilada mediante **/clr**), la imagen resultante será una imagen de modo mixto.

Puede usar **/CLRIMAGETYPE** para especificar un nivel inferior de capacidad de comprobación si es lo que necesita.

Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el nodo **Enlazador**.

1. Seleccione la página de propiedades **Avanzadas**.

1. Modifique la propiedad **Tipo de imagen de CLR**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
