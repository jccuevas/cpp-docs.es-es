---
title: Error irrecuperable del compilador de recursos RW1022 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caaefc045a31ca64aa9843927d550ef66285cb2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099855"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>Error irrecuperable del compilador de recursos RW1022

**Error al escribir archivo de E/S**

El compilador de recursos no pudo escribir en un archivo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Espacio en disco insuficiente. Espacio libre debe ser igual al menos dos veces el tamaño del archivo ejecutable que se va a crear.

1. El volumen es de solo lectura.

1. Sector defectuoso.

1. Infracción de uso compartido.