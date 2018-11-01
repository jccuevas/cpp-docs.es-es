---
title: Error de las herramientas del vinculador LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 137aa15dd9dad4b08d52af55da60a9cdf8b58055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662077"
---
# <a name="linker-tools-error-lnk1277"></a>Error de las herramientas del vinculador LNK1277

registro de objeto no encontrado en pgd (filename)

Cuando se usa [PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), la ruta de acceso de uno de los archivos .lib, def o .obj entrados era diferente de la ruta de acceso en el que se encontraron durante/LTCG: PGINSTRUMENT. Esto podría deberse a un cambio en la variable de entorno LIB después/LTCG: PGINSTRUMENT. La ruta de acceso completa a los archivos de entrada se almacena en el archivo PGD.

/ LTCG: PGOPTIMIZE requiere que las entradas sea idéntica a la fase/LTCG: PGINSTRUMENT.

Para resolver esta advertencia, realice una de las siguientes acciones:

- Ejecute/LTCG: PGINSTRUMENT, rehacer todas las ejecuciones de prueba y/LTCG: PGOPTIMIZE.

- Por lo que era cuando ejecutó/LTCG: PGINSTRUMENT, cambie la variable de entorno LIB.

No se recomienda evitar LNK1277 utilizando/LTCG: PGUPDATE.