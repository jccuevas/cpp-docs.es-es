---
title: 1.1 Ámbito
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449210"
---
# <a name="11-scope"></a>1.1 Ámbito

Esta especificación describe paralelización solo dirigido por el usuario, en la que el usuario especifica explícitamente las acciones que deben realizarse por el compilador y el sistema de tiempo de ejecución para ejecutar el programa en paralelo. Las implementaciones de OpenMP C y C++ no tienen que buscar dependencias, los conflictos, interbloqueos, condiciones de carrera u otros problemas que producen la ejecución del programa incorrecto. El usuario es responsable de garantizar que la aplicación con las construcciones OpenMP C y C++ API se ejecuta correctamente. Paralelización automáticas generadas por el compilador y las directivas del compilador para ayudar a dicha ejecución en paralelo no están cubiertas en este documento.