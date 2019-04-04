---
title: Crear un archivo .Sbr
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 6a2e685d33b108ce542fdc6e3e0565cc37299c1c
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508746"
---
# <a name="creating-an-sbr-file"></a>Crear un archivo .Sbr

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Los archivos de entrada para BSCMAKE son archivos. sbr. El compilador crea un archivo .sbr para cada archivo de objeto (.obj) lo compila. Al crear o actualizar el archivo de información de examen, todos los archivos .sbr para el proyecto deben estar disponibles en disco.

Para crear un archivo .sbr con toda la información posible, especifique [/FR](fr-fr-create-dot-sbr-file.md).

Para crear un archivo .sbr que no contenga símbolos locales, especifique [/Fr](fr-fr-create-dot-sbr-file.md). Si los archivos .sbr contienen símbolos locales, se puede omitir en el archivo .bsc mediante el uso de BSCMAKE [opción /El](bscmake-options.md)`.`

Puede crear un archivo .sbr sin realizar una compilación completa. Por ejemplo, puede especificar la opción /Zs al compilador que debe realizar una comprobación de sintaxis y seguirá generando un archivo .sbr si especifica /FR o/el fr.

El proceso de compilación puede ser más eficaz si los archivos .sbr se empaquetan en primer lugar para quitar las definiciones sin referencia. El compilador empaqueta automáticamente los archivos. sbr.

## <a name="see-also"></a>Vea también

[Crear un archivo .Bsc](building-a-dot-bsc-file.md)
