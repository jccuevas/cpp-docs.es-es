---
title: Error recuperable A2031 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf6744224847e114e76df6e7ad6470696d3e8387
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682663"
---
# <a name="ml-nonfatal-error-a2031"></a>Error recuperable A2031 de ML

**debe ser el registro de base o índice**

Se intentó usar un registro que no era un registro de base o índice en una expresión de la memoria.

Por ejemplo, las expresiones siguientes producen este error:

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>