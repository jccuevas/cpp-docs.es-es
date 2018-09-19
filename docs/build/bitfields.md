---
title: Campos de bits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7451ea6afee81cc296fb091705bde48041ef5d1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722493"
---
# <a name="bitfields"></a>Campos de bits

Campos de bits de estructura se limitan a 64 bits y puede ser de tipo con signo int, int sin signo, int64 o int64 sin signo. Campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo de bits para la alineación del tipo siguiente. Por ejemplo, los campos de bits de enteros no pueden cruzar un límite de 32 bits.

## <a name="see-also"></a>Vea también

[Tipos y almacenamiento](../build/types-and-storage.md)