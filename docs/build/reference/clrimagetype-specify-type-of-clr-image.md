---
title: /CLRIMAGETYPE (especificar el tipo de imagen CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5efb2e73e854591be7134753cec21a708fff3e5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705015"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Especificar tipo de imagen CLR)

Establecer el tipo de imagen CLR en la imagen vinculada.

## <a name="syntax"></a>Sintaxis

> **/ CLRIMAGETYPE:**{**IJW**|**PURO**|**SEGURO**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Comentarios

El vinculador acepta objetos nativos y también que se compilan mediante los objetos de MSIL [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). El **/CLR: pure** y **/CLR: safe** opciones del compilador ha quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017. Cuando se pasan objetos mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada. Por ejemplo, si se pasan una imagen nativa y una imagen de modo mixto (compilado mediante **/CLR**), la imagen resultante será una imagen de modo mixto.

Puede usar **/CLRIMAGETYPE** para especificar un nivel inferior de capacidad, si eso es lo que necesita.

Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](../../build/reference/clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** nodo.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **tipo de imagen CLR** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
