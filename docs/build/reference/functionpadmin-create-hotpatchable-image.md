---
title: /FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292400"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)

Prepara una imagen para aplicar una revisión activa.

## <a name="syntax"></a>Sintaxis

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>Argumentos

*space*<br/>
La cantidad de relleno que se agregará al principio de cada función en bytes. En x86 el valor predeterminado es 5 bytes de relleno y en x64 el valor predeterminado es 6 bytes. En otros destinos, debe proporcionarse un valor.

## <a name="remarks"></a>Comentarios

En orden para el vinculador generar una imagen a, los archivos .obj deben haberse compilados con [/hotpatch (crear una imagen)](hotpatch-create-hotpatchable-image.md).

Cuando se compila y vincula una imagen con una sola invocación de cl.exe, **/hotpatch** implica **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/FUNCTIONPADMIN** opción **opciones adicionales**. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
