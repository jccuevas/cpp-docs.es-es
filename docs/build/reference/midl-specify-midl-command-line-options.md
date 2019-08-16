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
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492723"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Especificar las opciones de la línea de comandos de MIDL)

Especifica un archivo de respuesta para las opciones de línea de comandos de MIDL

## <a name="syntax"></a>Sintaxis

> **/MIDL:\@** <em>archivo</em>

## <a name="arguments"></a>Argumentos

*file*<br/>
Nombre del archivo que contiene [las opciones](/windows/win32/Midl/general-midl-command-line-syntax)de la línea de comandos de MIDL.

## <a name="remarks"></a>Comentarios

Todas las opciones de conversión de un archivo IDL en un archivo TLB deben proporcionarse en el *archivo*; No se pueden especificar opciones de línea de comandos de MIDL en la línea de comandos del vinculador. Si no se especifica/MIDL, el compilador MIDL se invocará solo con el nombre de archivo IDL y sin otras opciones.

El archivo debe contener una opción de línea de comandos de MIDL por línea.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Página propiedades** > de configuración de**IDL incrustado** del**enlazador** > .

1. Modifique la propiedad **comandos MIDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[/IDLOUT (Dar nombre a los archivos de resultados de MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (No procesar atributos en MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Dar nombre a un archivo .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Compilación de programas con atributos](../../windows/building-an-attributed-program.md)
