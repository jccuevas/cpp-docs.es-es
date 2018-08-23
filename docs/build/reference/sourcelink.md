---
title: / SOURCELINK (archivo incluyen Sourcelink en PDB) | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /sourcelink
dev_langs:
- C++
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 876373b5646790f9f8de0042442b2ab56d9d2971
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "40242884"
---
# <a name="sourcelink-include-sourcelink-file-in-pdb"></a>/ SOURCELINK (archivo incluyen Sourcelink en PDB)

Especifica un archivo de configuración de SourceLink para incluir en el archivo PDB generado por el enlazador.

## <a name="syntax"></a>Sintaxis

> **/ SOURCELINK:**_nombre de archivo_

## <a name="arguments"></a>Argumentos

*filename*  
Especifica una configuración con formato JSON archivo que contiene una simple asignación de rutas de acceso local a direcciones URL donde se puede recuperar el archivo de origen para ser mostrado por el depurador. Para obtener más información sobre el formato de este archivo, consulte [esquema JSON de origen de vínculo](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Comentarios

SourceLink es un sistema de control de código fuente y de idioma independiente para proporcionar la depuración de código fuente para los archivos binarios. Archivos binarios nativos de C++ a partir de Visual Studio 2017 versión 15,8 es compatible con SourceLink. Para obtener información general de SourceLink, consulte [Sourcelink](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Para obtener información sobre cómo usar SourceLink en los proyectos y cómo generar el archivo de SourceLink como parte del proyecto, vea [SourceLink utilizando](https://github.com/dotnet/sourcelink#using-sourcelink).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador /SOURCELINK en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/SOURCELINK:**_filename_ y, a continuación, elija **Aceptar** o **aplicar**para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
- Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
