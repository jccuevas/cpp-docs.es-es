---
title: Las herramientas del vinculador LNK1277 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082544"
---
# <a name="linker-tools-error-lnk1277"></a>Error de las herramientas del vinculador LNK1277

registro de objeto no encontrado en pgd (filename)

Cuando se usa [PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), la ruta de acceso de uno de los archivos .lib, def o .obj entrados era diferente de la ruta de acceso en el que se encontraron durante/LTCG: PGINSTRUMENT. Esto podría deberse a un cambio en la variable de entorno LIB después/LTCG: PGINSTRUMENT. La ruta de acceso completa a los archivos de entrada se almacena en el archivo PGD.

/ LTCG: PGOPTIMIZE requiere que las entradas sea idéntica a la fase/LTCG: PGINSTRUMENT.

Para resolver esta advertencia, realice una de las siguientes acciones:

- Ejecute/LTCG: PGINSTRUMENT, rehacer todas las ejecuciones de prueba y/LTCG: PGOPTIMIZE.

- Por lo que era cuando ejecutó/LTCG: PGINSTRUMENT, cambie la variable de entorno LIB.

No se recomienda evitar LNK1277 utilizando/LTCG: PGUPDATE.