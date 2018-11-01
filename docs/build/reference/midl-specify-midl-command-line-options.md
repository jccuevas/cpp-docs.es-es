---
title: /MIDL (Especificar las opciones de la línea de comandos de MIDL)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: 273e4ea5776c0de5af16eba235c5775d6f4c4b54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525575"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Especificar las opciones de la línea de comandos de MIDL)

Especifica un archivo de respuesta para las opciones de línea de comandos MIDL

## <a name="syntax"></a>Sintaxis

> **/ MIDL:\@**<em>archivo</em>

## <a name="arguments"></a>Argumentos

*file*<br/>
El nombre del archivo que contiene [las opciones de línea de comandos MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Comentarios

Todas las opciones para la conversión de un archivo IDL en archivo TLB deben proporcionarse en *archivo*; No se puede especificar las opciones de línea de comandos de MIDL en línea de comandos del vinculador. Si no se especifica /MIDL, se invocará el compilador de MIDL con solo el nombre de archivo IDL y ninguna otra opción.

El archivo debe contener una opción de línea de comandos de MIDL por línea.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **IDL incrustado** página de propiedades.

1. Modificar el **comandos MIDL** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[/IDLOUT (Dar nombre a los archivos de resultados de MIDL)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (No procesar atributos en MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Dar nombre a un archivo .TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[Compilación de programas con atributos](../../windows/building-an-attributed-program.md)
