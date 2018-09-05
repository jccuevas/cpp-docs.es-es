---
title: Error recuperable A2219 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2219
dev_langs:
- C++
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 365997181b0d4f4471162d7cf8f65a4429e69e74
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681650"
---
# <a name="ml-nonfatal-error-a2219"></a>Error recuperable A2219 de ML

**Alineación incorrecta de desplazamiento en el código de desenredado**

El operando para [. ALLOCSTACK](../../assembler/masm/dot-allocstack.md) y [. SAVEREG](../../assembler/masm/dot-savereg.md) debe ser un múltiplo de 8.  El operando para [. Savexmm128](../../assembler/masm/dot-savexmm128.md) y [. SETFRAME](../../assembler/masm/dot-setframe.md) debe ser un múltiplo de 16.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>