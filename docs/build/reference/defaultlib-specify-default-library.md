---
title: /DEFAULTLIB (Especificar biblioteca predeterminada) | Documentos de Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9afcaa0e229ec34ba91b4d60a7a4fa9acec2d7e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569786"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Especificar la biblioteca predeterminada)

Especifique una biblioteca predeterminada búsqueda para resolver referencias externas.

## <a name="syntax"></a>Sintaxis

> **/ DEFAULTLIB**:_biblioteca_

### <a name="arguments"></a>Argumentos

|Argumento|Descripción|
|-|-|
*Biblioteca de*|El nombre de una biblioteca para buscar al resolver referencias externas.

## <a name="remarks"></a>Comentarios

El **DEFAULTLIB** opción agrega una *biblioteca* a la lista de bibliotecas que LINK busca durante la resolución de referencias. Una biblioteca especificada con **DEFAULTLIB** se busca después de las bibliotecas que se especifican explícitamente en la línea de comandos y antes de las bibliotecas predeterminadas mencionadas en los archivos .obj.

Cuando se utiliza sin argumentos, la [/NODEFAULTLIB (omitir todas las bibliotecas predeterminadas)](../../build/reference/nodefaultlib-ignore-libraries.md) opción invalida all **DEFAULTLIB**:*biblioteca* opciones. El **/NODEFAULTLIB**:*biblioteca* opción invalidaciones **DEFAULTLIB**:*biblioteca* cuando el mismo *biblioteca*nombre se especifica en ambos.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba un **DEFAULTLIB**:*biblioteca* opción para cada biblioteca buscar. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
