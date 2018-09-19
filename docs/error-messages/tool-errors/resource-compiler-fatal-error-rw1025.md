---
title: Error irrecuperable del compilador de recursos RW1025 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf7bdeed320c004ffb75fa1d25d9b89147b0c13
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117405"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Error irrecuperable del compilador de recursos RW1025

Memoria de montón far insuficiente

Compruebe si hay software residente en memoria que puede ocupar mucho espacio. Utilice el programa CHKDSK para averiguar cuánta memoria tiene.

Si va a crear un archivo de recursos grandes, divida el script de recursos en dos archivos. Después de crear dos archivos, use la línea de comandos de MS-DOS para combinarlas:

```
copy first.res /b + second.res /b full.res
```