---
title: /SOURCELINK (Incluir archivo Sourcelink en PDB)
description: Guía de referencia para la opción del vinculador /SOURCELINK en Microsoft C++.
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336070"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (Incluir archivo de vínculo de origen en PDB)

Especifica un archivo de configuración de vínculo de origen que se incluirá en el archivo PDB generado por el vinculador.

## <a name="syntax"></a>Sintaxis

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>Argumentos

*Nombre*<br/>
Especifica un archivo de configuración con formato JSON que contiene una asignación sencilla de rutas de acceso de archivo local a direcciones URL para que los archivos de origen se muestren en el depurador. Para obtener más información sobre el formato de este archivo, vea [Esquema JSON](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema)de vínculo de origen .

## <a name="remarks"></a>Observaciones

Source Link es un sistema agnóstico de control de código fuente y lenguaje para proporcionar depuración de origen para archivos binarios. El vínculo de origen se admite para los archivos binarios nativos de C++ a partir de Visual Studio 2017 versión 15.8. Para obtener información general sobre el vínculo de origen, consulte vínculo de [origen](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md). Para obtener información sobre cómo usar el vínculo de origen en los proyectos y cómo generar el archivo SourceLink como parte del proyecto, consulte Uso del vínculo de [origen](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador /SOURCELINK en Visual Studio

1. Abra el cuadro de diálogo **Páginas** de propiedades del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades de la línea de**comandos** del**vinculador** > de propiedades > de **configuración.**

1. En el cuadro Opciones **`/SOURCELINK:`** _`filename`_ **adicionales,** agregue y, a continuación, elija **Aceptar** o **Aplicar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente programático.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones de MSVC Linker](linker-options.md)
