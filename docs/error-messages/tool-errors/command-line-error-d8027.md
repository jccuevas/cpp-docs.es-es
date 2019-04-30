---
title: Error de la línea de comandos D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214186"
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