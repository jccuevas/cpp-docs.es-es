---
title: /CLRIMAGETYPE (Especificar tipo de imagen CLR)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: b2a6df0f778ba079bffefeeacdad22cb398a529a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820681"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Especificar tipo de imagen CLR)

Establezca el tipo de imagen CLR de la imagen vinculada.

## <a name="syntax"></a>Sintaxis

> **/CLRIMAGETYPE:**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Comentarios

El vinculador acepta objetos nativos y también los objetos que se compilan con MSIL [/CLR](clr-common-language-runtime-compilation.md). El **/CLR: pure** y **/CLR: safe** opciones del compilador han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017. Cuando se pasan objetos mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada. Por ejemplo, si se pasan una imagen nativa y una imagen de modo mixto (compilado mediante **/CLR**), la imagen resultante será una imagen de modo mixto.

Puede usar **/CLRIMAGETYPE** para especificar un nivel inferior de verificabilidad, si eso es lo que necesita.

Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **tipo de imagen CLR** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Vea también

- [Referencia MSVC del vinculador](linking.md)
- [Opciones del vinculador MSVC](linker-options.md)
