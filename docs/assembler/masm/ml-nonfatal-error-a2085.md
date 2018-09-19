---
title: Error recuperable A2085 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681441"
---
# <a name="ml-nonfatal-error-a2085"></a>Error recuperable A2085 de ML

**instrucción o registrar que no se acepta en modo de CPU actual**

Se intentó utilizar una instrucción, el registro o la palabra clave que no era válido para el modo actual del procesador.

Por ejemplo, registros de 32 bits requieren [.386](../../assembler/masm/dot-386.md) o superior. Registros de control, como CR0 requieren el modo privilegiado [.386P](../../assembler/masm/dot-386p.md) o superior. Este error también se generarán para el **NEAR32**, **FAR32**, y **planos** palabras clave, que requieren. **386** o superior.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>