---
title: Error de las herramientas del vinculador LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194751"
---
# <a name="linker-tools-error-lnk2013"></a>Error de las herramientas del vinculador LNK2013

Desbordamiento de la corrección tipo de corrección. 'symbol name' de destino fuera del intervalo

El vinculador no puede ajustar la dirección o desplazamiento requeridos en la instrucción dada, porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.

Puede resolver este problema mediante la creación de varias imágenes o mediante la opción [/Order](../../build/reference/order-put-functions-in-order.md) , de modo que la instrucción y el destino estén más juntos.

Cuando el nombre del símbolo es un símbolo definido por el usuario (y no uno generado por el compilador) también pueden probarse las siguientes acciones para resolver el error:

- Cambiar la función estática para que no sea estática.

- Cambiar el nombre de la sección de código que contiene la función estática para que sea el mismo que el de la sección que realiza la llamada.

Utilice `DUMPBIN /SYMBOLS` para ver si una función es estática.
