---
title: Cómo compila BSCMAKE un archivo .Bsc
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: e691e6ee2dcda0fb04735705078f1ed2ff139301
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425593"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Cómo compila BSCMAKE un archivo .Bsc

BSCMAKE genera o vuelve a generar un archivo .bsc en la forma más eficaz que sea posible. Para evitar posibles problemas, es importante comprender el proceso de compilación.

Cuando BSCMAKE genera un archivo de información de examen, trunca los archivos .sbr longitud cero. Durante una compilación posterior del mismo archivo, un archivo .sbr de longitud cero (o vacío) indica a BSCMAKE que el archivo .sbr no tiene ninguna contribución nuevo a realizar. Permite saber que no se requiere una actualización de la parte del archivo y una compilación incremental será suficiente BSCMAKE. Durante cada compilación (a menos que se ha especificado la opción/n), BSCMAKE primero intenta actualizar el archivo de forma incremental con sólo los archivos .sbr que han cambiado.

BSCMAKE busca un archivo .bsc que tiene el nombre especificado con la opción/o. Si no se especifica/o, BSCMAKE busca un archivo que tiene el nombre base del primer archivo .sbr y una extensión de BSC. Si el archivo existe, BSCMAKE realiza una compilación incremental del archivo de información de exploración utilizando sólo los archivos .sbr participantes. Si el archivo no existe, BSCMAKE realiza una compilación completa con todos los archivos. sbr. Las reglas para las compilaciones son los siguientes:

- Para que una compilación completa se realice correctamente, todos los especificados los archivos .sbr deben existir y no se deben truncar. Si se trunca un archivo .sbr, debe recompilar (por volver a compilar o ensamblar) antes de ejecutar BSCMAKE.

- Para que una compilación incremental se realice correctamente, debe existir el archivo .bsc. Todos los archivos .sbr participantes, incluso los archivos vacíos, debe existir y debe especificarse en la línea de comandos BSCMAKE. Si se omite un archivo .sbr desde la línea de comandos, BSCMAKE quita su contribución del archivo.

## <a name="see-also"></a>Vea también

[Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)
