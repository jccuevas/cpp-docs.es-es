---
title: Error irrecuperable C1902 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 89354565f67c8704eee8c8b5f9dcb94523800c63
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1902"></a>Error irrecuperable C1902
Error de coincidencia de administrador de base de datos de programa; Compruebe la instalación  
  
Un archivo de base de datos de programa (.pdb) se creó con una versión más reciente de mspdb*XXX*dll a la que el compilador ha encontrado en el sistema. Este error suele indicar que mspdbsrv.exe o mspdbcore.dll falta o tiene versiones diferentes que mspdb*XXX*.dll. (El *XXX* marcador de posición en la mspdb*XXX*cambios de nombre de archivo .dll con cada versión del producto. Por ejemplo, en Visual Studio 2015, el nombre de archivo es mspdb140.dll).  
  
Asegúrese de versiones coincidentes de mspdbsrv.exe, mspdbcore.dll y mspdb*XXX*.dll están instalados en el sistema. Asegúrese de que las versiones no coinciden no se han copiado en el directorio que contiene las herramientas del compilador y el vínculo correspondiente a su plataforma de destino. Por ejemplo, es posible que haya copiado los archivos para poder invocar la herramienta de compilador o vínculo desde el símbolo del sistema sin establecer el **ruta de acceso** variable de entorno en consecuencia.
