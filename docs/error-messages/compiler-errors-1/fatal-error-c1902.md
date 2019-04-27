---
title: Error irrecuperable C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165871"
---
# <a name="fatal-error-c1902"></a>Error irrecuperable C1902

Error de coincidencia de administrador de base de datos de programa; Compruebe la instalación

Un archivo de base de datos de programa (.pdb) se creó con una versión más reciente de mspdb*XXX*.dll a la que el compilador ha encontrado en el sistema. Este error suele indicar que mspdbsrv.exe o mspdbcore.dll faltan o tienen versiones diferentes de mspdb*XXX*.dll. (El *XXX* marcador de posición en el mspdb*XXX*cambios de nombre de archivo .dll con cada versión del producto. Por ejemplo, en Visual Studio 2015, el nombre de archivo es mspdb140.dll).

Asegúrese de versiones coincidentes de mspdbsrv.exe, mspdbcore.dll y mspdb*XXX*.dll están instalados en el sistema. Asegúrese de que no se han copiado al directorio que contiene las herramientas del compilador y vínculo para la plataforma de destino las versiones no coinciden. Por ejemplo, es posible que haya copiado los archivos para poder invocar la herramienta de compilador o un vínculo desde el símbolo del sistema sin establecer el **ruta** variable de entorno en consecuencia.