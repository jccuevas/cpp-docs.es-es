---
title: Campos de bits
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
ms.openlocfilehash: 3ff0092bbd31b8b1cd98fa56fb802c7ce28cb472
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652834"
---
# <a name="bitfields"></a>Campos de bits

Campos de bits de estructura se limitan a 64 bits y puede ser de tipo con signo int, int sin signo, int64 o int64 sin signo. Campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo de bits para la alineación del tipo siguiente. Por ejemplo, los campos de bits de enteros no pueden cruzar un límite de 32 bits.

## <a name="see-also"></a>Vea también

[Tipos y almacenamiento](../build/types-and-storage.md)