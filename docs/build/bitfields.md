---
title: Campos de bits | Documentos de Microsoft
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
ms.openlocfilehash: 85db49f138cc733326e47a3008e79bae5ab4b7cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="bitfields"></a>Campos de bits
Campos de bits de estructura se limitan a 64 bits y pueden ser de tipo con signo int, int sin signo, int64 o int64 sin signo. Los campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo de bits para la alineación de tipo siguiente. Por ejemplo, los campos de bits de enteros no pueden cruzar un límite de 32 bits.  
  
## <a name="see-also"></a>Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)