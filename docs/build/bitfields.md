---
title: Campos de bits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 231d84e5d99cd9e6c1238ae12c143636f62ce80d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bitfields"></a>Campos de bits
Campos de bits de estructura se limitan a 64 bits y pueden ser de tipo con signo int, int sin signo, int64 o int64 sin signo. Los campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo de bits para la alineación de tipo siguiente. Por ejemplo, los campos de bits de enteros no pueden cruzar un límite de 32 bits.  
  
## <a name="see-also"></a>Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)