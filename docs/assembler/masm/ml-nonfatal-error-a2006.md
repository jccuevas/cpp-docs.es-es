---
title: Error recuperable A2006 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d2f7df00d1c0658ee8301fbde1efe2522b52fc
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2006"></a>Error recuperable A2006 de ML
**símbolo no definido: identificador**  
  
 Se intentó usar un símbolo que no se ha definido.  
  
 Puede haberse producido uno de los siguientes:  
  
-   No se definió un símbolo.  
  
-   Un campo no es un miembro de la estructura especificada.  
  
-   Se definió un símbolo en un archivo de inclusión que no se incluyó.  
  
-   Se utilizó un símbolo externo sin un [EXTERN](../../assembler/masm/extern-masm.md) o [EXTERNDEF](../../assembler/masm/externdef.md) directiva.  
  
-   Un nombre de símbolo se escribió correctamente.  
  
-   Se hizo referencia a una etiqueta de código local fuera de su ámbito.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)