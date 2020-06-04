---
title: Error de las herramientas del vinculador LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183662"
---
# <a name="linker-tools-error-lnk1277"></a>Error de las herramientas del vinculador LNK1277

no se encontró el registro de objeto en PGD (nombre de archivo)

Al usar [/LTCG: PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), la ruta de acceso de uno de los archivos Input. lib, Def o. obj es diferente de la ruta de acceso en la que se encontraron durante/LTCG: PGINSTRUMENT. Esto puede explicarse mediante un cambio en la variable de entorno LIB después de/LTCG: PGINSTRUMENT. La ruta de acceso completa a los archivos de entrada se almacena en el archivo. PGD.

/LTCG: PGOPTIMIZE requiere que las entradas sean idénticas a la fase/LTCG: PGINSTRUMENT.

Para resolver esta advertencia, realice una de las acciones siguientes:

- Ejecute/LTCG: PGINSTRUMENT, rehaga todas las ejecuciones de pruebas y ejecute/LTCG: PGOPTIMIZE.

- Cambie la variable de entorno LIB a lo que estaba cuando ejecutó/LTCG: PGINSTRUMENT.

No se recomienda trabajar en torno a LNK1277 mediante/LTCG: PGUPDATE.
