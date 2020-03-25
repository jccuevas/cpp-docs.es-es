---
title: Advertencia de las herramientas del vinculador LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 43fae7d0f19f96998d2e1a1739bc3e596bbd9ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194205"
---
# <a name="linker-tools-warning-lnk4037"></a>Advertencia de las herramientas del vinculador LNK4037

>'*Symbol*' no existe; tendrán

No se pudo ordenar el *símbolo* de nombre representativo mediante la opción [/Order](../../build/reference/order-put-functions-in-order.md) porque no se encontró en el programa. Compruebe la especificación del *símbolo* en el archivo de respuesta de pedido. Para obtener más información, vea la opción del enlazador [/Order (Put Functions en orden)](../../build/reference/order-put-functions-in-order.md) .

> [!NOTE]
> LINK no puede ordenar funciones estáticas porque los nombres de funciones estáticas no son nombres de símbolos públicos. Cuando se especifica **/Order** , se genera esta advertencia del vinculador para cada símbolo del archivo de respuesta de pedido que sea estático o no se encuentre.
