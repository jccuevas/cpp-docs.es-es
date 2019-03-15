---
title: /ALIGN (Alineación de sección)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: d8d2e6a859c68af473d49dc04b76f0a15056aa56
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57809475"
---
# <a name="align-section-alignment"></a>/ALIGN (Alineación de sección)

## <a name="syntax"></a>Sintaxis

> **/ALIGN**[**:**_number_]

### <a name="arguments"></a>Argumentos

*number*<br/>
El valor de alineación en bytes.

## <a name="remarks"></a>Comentarios

El **/alinear** opción especifica la alineación de cada sección en el espacio de direcciones lineales del programa. El *número* argumento está en bytes y debe ser una potencia de dos. El valor predeterminado es 4 KB (4096). El enlazador emite una advertencia si la alineación produce una imagen no válida.

A menos que se está escribiendo una aplicación como un controlador de dispositivo, no es necesario modificar la alineación.

Es posible modificar la alineación de una sección determinada con el parámetro de alineación del [/SECTION](section-specify-section-attributes.md) opción.

El valor de alineación que especifique no puede ser menor que la alineación de sección mayor.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Especifique la opción en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
