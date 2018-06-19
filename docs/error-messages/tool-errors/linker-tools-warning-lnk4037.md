---
title: Las herramientas del vinculador LNK4037 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302440"
---
# <a name="linker-tools-warning-lnk4037"></a>Herramientas del vinculador LNK4037 de advertencia

>'*símbolo*' no existe; se omitió

El nombre representativo *símbolo* no se puede ordenar mediante el uso de la [/orden](../../build/reference/order-put-functions-in-order.md) opción porque no se encontró en el programa. Compruebe la especificación de *símbolo* en el archivo de respuesta de pedido. Para obtener más información, consulte el [/Order (Put funciones en orden)](../../build/reference/order-put-functions-in-order.md) opción del vinculador.

> [!NOTE]
> VÍNCULO no puede ordenar las funciones estáticas porque los nombres de función estática no son nombres de símbolos públicos. Cuando **/orden** se ha especificado, esta advertencia del vinculador se genera para cada símbolo en el archivo de respuesta de orden que sea estático o no se encuentra.