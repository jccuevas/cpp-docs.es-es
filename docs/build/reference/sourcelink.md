---
title: / SOURCELINK (archivo incluyen Sourcelink en PDB)
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: a5a01ca56a49791a608c5c836312c7728e9328c3
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978288"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/ SOURCELINK (archivo incluir vínculo de origen en el archivo PDB)

Especifica un archivo de configuración de vínculo de origen debe incluir en el archivo PDB generado por el enlazador.

## <a name="syntax"></a>Sintaxis

> **/ SOURCELINK:**_nombre de archivo_

## <a name="arguments"></a>Argumentos

*filename*<br/>
Especifica una configuración con formato JSON archivo que contiene una simple asignación de rutas de acceso local a direcciones URL donde se puede recuperar el archivo de origen para ser mostrado por el depurador. Para obtener más información sobre el formato de este archivo, consulte [esquema JSON de origen de vínculo](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Comentarios

Vínculo de origen es un sistema de control de código fuente y de idioma independiente para proporcionar la depuración de código fuente para los archivos binarios. Vínculo de origen es compatible con archivos binarios nativos de C++ a partir de Visual Studio 2017 versión 15,8. Para obtener información general de vínculo de origen, consulte [Sourcelink](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Para obtener información sobre cómo usar el vínculo de origen en los proyectos y cómo generar el archivo de SourceLink como parte del proyecto, vea [Sourcelink utilizando](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador /SOURCELINK en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/SOURCELINK:**_filename_ y, a continuación, elija **Aceptar** o **aplicar**para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
