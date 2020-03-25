---
title: Error irrecuperable C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: 10a411dfc942498a98959d9a23cb42dfb93cf2ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202831"
---
# <a name="fatal-error-c1902"></a>Error irrecuperable C1902

Administrador de base de datos de programa no coincidente; Compruebe la instalación.

Un archivo de base de datos de programa (. pdb) se creó con una versión más reciente de mspdb*XXX*. dll que la que el compilador encontró en el sistema. Este error suele indicar que falta mspdbsrv. exe o mspdbcore. dll o que tiene versiones diferentes de mspdb*XXX*. dll. (El marcador de posición *XXX* en el nombre de archivo mspdb*XXX*. dll cambia con cada versión del producto. Por ejemplo, en Visual Studio 2015, el nombre de archivo es mspdb140. dll).

Asegúrese de que las versiones de mspdbsrv. exe, mspdbcore. dll y mspdb*XXX*. dll estén instaladas en el sistema. Asegúrese de que las versiones no coincidentes no se han copiado en el directorio que contiene el compilador y las herramientas de vínculo para la plataforma de destino. Por ejemplo, es posible que haya copiado los archivos para poder invocar el compilador o la herramienta de vinculación desde el símbolo del sistema sin establecer la variable de entorno **path** en consecuencia.
