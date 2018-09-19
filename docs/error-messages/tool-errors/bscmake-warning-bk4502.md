---
title: Advertencia de BSCMAKE BK4502 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4142993b3f4f5bda2b3e4ce322aa26d7beca8584
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056331"
---
# <a name="bscmake-warning-bk4502"></a>Advertencia de BSCMAKE BK4502

truncado. Archivos SBR 'filename' no está en nombre de archivo

Se especificó un archivo .sbr de longitud cero que inicialmente no formaba parte de un archivo .bsc durante una actualización.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Especificadas el nombre de archivo incorrecto.

1. Archivo eliminado. (Error [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) resultados.)

1. Archivo dañado, que requieren BSCMAKE que realice una compilación completa.