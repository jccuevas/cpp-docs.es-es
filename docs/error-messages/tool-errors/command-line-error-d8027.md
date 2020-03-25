---
title: Error de la línea de comandos D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196890"
---
# <a name="command-line-error-d8027"></a>Error de la línea de comandos D8027

no se puede ejecutar ' Component '

El compilador no pudo ejecutar el enlazador o componente de compilador especificado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. No hay suficiente memoria para cargar el componente. Si NMAKE invocó el compilador, ejecute el compilador fuera del archivo make.

1. El sistema operativo actual no pudo ejecutar el componente. Asegúrese de que la ruta de acceso señala a los archivos ejecutables adecuados para su sistema operativo.

1. El componente está dañado. Recopie el componente desde los discos de distribución mediante el programa de instalación.

1. Se especificó incorrectamente una opción. Por ejemplo:

    ```
    cl /B1 file1.c
    ```
