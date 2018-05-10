---
title: 1.1 ámbito | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="11-scope"></a>1.1 Ámbito
Esta especificación cubre dirigido por el usuario sólo la ejecución en paralelo, en el que el usuario especifica explícitamente las acciones a emprender por el compilador y el sistema en tiempo de ejecución con el fin de ejecutar el programa en paralelo. Implementaciones de OpenMP C y C++ no tienen que buscar dependencias, está en conflicto, interbloqueos, condiciones de carrera u otros problemas que son el resultado de la ejecución del programa incorrecto. El usuario es responsable de garantizar que la aplicación con las construcciones OpenMP C y C++ API se ejecuta correctamente. Ejecución en paralelo automática generada por el compilador y directivas para el compilador para ayudar a dicha ejecución en paralelo no se tratan en este documento.