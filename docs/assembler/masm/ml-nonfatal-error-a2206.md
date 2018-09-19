---
title: Error recuperable A2206 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2206
dev_langs:
- C++
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10edbe68ca7f0093cdeb6a9ca5a02cde07f556e6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676353"
---
# <a name="ml-nonfatal-error-a2206"></a>Error recuperable A2206 de ML

**Falta el operador de expresión**

No se puede evaluar la expresión porque falta un operador. Este mensaje de error también puede ser un efecto secundario de un error en un programa anterior.

La línea siguiente generará este error:

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>