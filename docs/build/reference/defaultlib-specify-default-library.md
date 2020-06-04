---
title: /DEFAULTLIB (Especificar la biblioteca predeterminada)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 0b7d4569c7be70bd97094ebbe09a7ae462331983
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293867"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Especificar la biblioteca predeterminada)

Especifique una biblioteca predeterminada donde buscar para resolver referencias externas.

## <a name="syntax"></a>Sintaxis

> **/DEFAULTLIB**:_library_

### <a name="arguments"></a>Argumentos

*library*<br/>
El nombre de una biblioteca para buscar al resolver referencias externas.

## <a name="remarks"></a>Comentarios

El **DEFAULTLIB** agrega una opción *biblioteca* a la lista de bibliotecas de vínculo realiza búsquedas al resolver referencias. Una biblioteca especificada con **DEFAULTLIB** después de las bibliotecas especificadas explícitamente en la línea de comandos y antes de las bibliotecas predeterminadas mencionadas en los archivos .obj se va a buscar.

Cuando se utiliza sin argumentos, el [/NODEFAULTLIB (omitir todas las bibliotecas predeterminadas)](nodefaultlib-ignore-libraries.md) opción invalida todos **DEFAULTLIB**:*biblioteca* opciones. El **/NODEFAULTLIB**:*biblioteca* opción invalidaciones **DEFAULTLIB**:*biblioteca* cuando el mismo *biblioteca*nombre se especifica en ambos.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba un **DEFAULTLIB**:*biblioteca* opción para cada biblioteca buscar. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
