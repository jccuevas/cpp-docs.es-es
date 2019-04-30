---
title: Advertencia de las herramientas del vinculador LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410309"
---
# <a name="linker-tools-warning-lnk4037"></a>Advertencia de las herramientas del vinculador LNK4037

>'*símbolo*' no existe; se ha omitido

El nombre representativo *símbolo* no se pudo ordenar mediante el uso de la [/Order](../../build/reference/order-put-functions-in-order.md) opción porque no se encontró en el programa. Compruebe la especificación de *símbolo* en el archivo de respuesta de pedido. Para obtener más información, consulte el [/ORDER (colocar funciones en orden)](../../build/reference/order-put-functions-in-order.md) opción del vinculador.

> [!NOTE]
> VÍNCULO no puede ordenar las funciones estáticas porque los nombres de función estático no son nombres de símbolos públicos. Cuando **/Order** se especifica, se genera esta advertencia del vinculador para cada símbolo en el archivo de respuesta de pedido que sea estático o no se encuentra.