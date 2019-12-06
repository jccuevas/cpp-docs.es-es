---
title: /NOPDB
description: La opción/NOPDB evita que DUMPBIN cargue y busque la información de símbolos en los archivos PDB.
ms.date: 12/04/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 7b0c01e59b52bcec6ddf09416dd6aac9999527a6
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856974"
---
# <a name="nopdb"></a>/NOPDB

Indica a DUMPBIN que no cargue y busque en los archivos de base de datos de programa (PDB) la información de símbolos.

## <a name="syntax"></a>Sintaxis

> **/NOPDB**

## <a name="remarks"></a>Notas

De forma predeterminada, DUMPBIN intenta cargar archivos PDB para sus ejecutables de destino. DUMPBIN usa esta información para buscar coincidencias con las direcciones de los nombres de símbolos. El proceso puede llevar mucho tiempo si los archivos PDB son grandes o se deben cargar desde un servidor remoto. La opción **/NOPDB** indica a DUMPBIN que omita este paso. Solo imprime la información de direcciones y símbolos disponible en el archivo ejecutable.

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador/NOPDB en Visual Studio

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **Enlazador** > **Línea de comandos**.

1. En el cuadro **opciones adicionales** , agregue la opción **/NOPDB** . Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente de programación.

## <a name="see-also"></a>Vea también

\ de [línea de comandos de DUMPBIN](dumpbin-command-line.md)
[Opciones de DUMPBIN](dumpbin-options.md)\
[Referencia de DUMPBIN](dumpbin-reference.md)
