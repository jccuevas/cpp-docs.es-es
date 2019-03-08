---
title: Variables de entorno de LINK
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
ms.openlocfilehash: 03f84ea1071a672aef4443e5acf44daae91bb3b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422144"
---
# <a name="link-environment-variables"></a>Variables de entorno de LINK

La herramienta LINK usa las variables de entorno siguientes:

- VÍNCULO y \_vínculo\_, si ha definido. La herramienta LINK antepone las opciones y argumentos definidos en la variable de entorno LINK y anexa las opciones y argumentos definan en el \_vínculo\_ variable de entorno para los argumentos de línea de comandos antes del procesamiento.

- LIB, si se define. La herramienta LINK usa la ruta de acceso LIB para buscar un objeto, biblioteca u otro archivo especificado en la línea de comandos o mediante el [/base](../../build/reference/base-base-address.md) opción. También usa esta ruta para buscar un archivo .pdb denominado en un objeto. La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma. Una ruta de acceso debe apuntar al subdirectorio \lib de la instalación de Visual C++.

- PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK. (LINK requiere CVTRES para vincular un archivo. res). PATH debe apuntar al subdirectorio \bin de la instalación de Visual C++.

- TMP, para especificar un directorio al vincular archivos .res u OMF.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[Compilación de código de C o C++ en la línea de comandos](../../build/building-on-the-command-line.md)<br/>
[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
