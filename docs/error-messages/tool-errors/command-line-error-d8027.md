---
title: Error de la línea de comandos D8027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8234835d3bb0545c8a72bf35cfb55b2e18bc7da2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070384"
---
# <a name="command-line-error-d8027"></a>Error de la línea de comandos D8027

no se puede ejecutar 'componente'

El compilador no pudo ejecutar el componente del compilador dado o vinculador.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. No hay suficiente memoria para cargar el componente. Si NMAKE invoca el compilador, ejecutar el compilador fuera del archivo MAKE.

1. El sistema operativo actual no pudo ejecutar el componente. Asegúrese de que los puntos de ruta de acceso a los archivos ejecutables apropiados para su sistema operativo.

1. El componente está dañado. Volver a copiar el componente de los discos de distribución mediante el programa de instalación.

1. Se especificó una opción incorrectamente. Por ejemplo:

    ```
    cl /B1 file1.c
    ```