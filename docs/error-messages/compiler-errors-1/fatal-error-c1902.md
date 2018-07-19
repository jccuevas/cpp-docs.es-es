---
title: Error irrecuperable C1902 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23507b6531f9ee4e5ce5efd5b60a1977206635c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228204"
---
# <a name="fatal-error-c1902"></a>Error irrecuperable C1902
Error de coincidencia de administrador de base de datos de programa; Compruebe la instalación  
  
Un archivo de base de datos de programa (.pdb) se creó con una versión más reciente de mspdb*XXX*dll a la que el compilador ha encontrado en el sistema. Este error suele indicar que mspdbsrv.exe o mspdbcore.dll falta o tiene versiones diferentes que mspdb*XXX*.dll. (El *XXX* marcador de posición en la mspdb*XXX*cambios de nombre de archivo .dll con cada versión del producto. Por ejemplo, en Visual Studio 2015, el nombre de archivo es mspdb140.dll).  
  
Asegúrese de versiones coincidentes de mspdbsrv.exe, mspdbcore.dll y mspdb*XXX*.dll están instalados en el sistema. Asegúrese de que las versiones no coinciden no se han copiado en el directorio que contiene las herramientas del compilador y el vínculo correspondiente a su plataforma de destino. Por ejemplo, es posible que haya copiado los archivos para poder invocar la herramienta de compilador o vínculo desde el símbolo del sistema sin establecer el **ruta de acceso** variable de entorno en consecuencia.