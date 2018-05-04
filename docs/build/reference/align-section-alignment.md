---
title: /ALIGN (alineación de sección) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs:
- C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 543ea30b06f62939f378167d8598c73f66061f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="align-section-alignment"></a>/ALIGN (Alineación de sección)

## <a name="syntax"></a>Sintaxis

> **/ ALINEAR**[**:**_número_]

### <a name="arguments"></a>Argumentos

*Número*  
El valor de alineación en bytes.

## <a name="remarks"></a>Comentarios

El **/alinear** opción especifica la alineación de cada sección en el espacio de direcciones lineales del programa. El *número* argumento está en bytes y debe ser una potencia de dos. El valor predeterminado es 4K (4096). El vinculador emite una advertencia si la alineación produce una imagen no válida.

A menos que se está escribiendo una aplicación como un controlador de dispositivo, no es necesario modificar la alineación.

Es posible modificar la alineación de una sección determinada con el parámetro de alinear a la [/SECTION](../../build/reference/section-specify-section-attributes.md) opción.

El valor de alineación especificado no puede ser menor que la alineación de sección más grande.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en la **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
