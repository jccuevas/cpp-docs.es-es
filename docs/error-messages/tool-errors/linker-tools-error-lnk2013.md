---
title: Error de las herramientas del vinculador LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620734"
---
# <a name="linker-tools-error-lnk2013"></a>Error de las herramientas del vinculador LNK2013

Desbordamiento de la corrección tipo de corrección. 'symbol name' de destino fuera del intervalo

El vinculador no puede ajustar la dirección o desplazamiento requeridos en la instrucción dada, porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.

Puede resolver este problema creando varias imágenes o mediante el [/Order](../../build/reference/order-put-functions-in-order.md) opción para la instrucción y el destino estén más cerca.

Cuando el nombre del símbolo es un símbolo definido por el usuario (y no uno generado por el compilador) también pueden probarse las siguientes acciones para resolver el error:

- Cambiar la función estática para que no sea estática.

- Cambiar el nombre de la sección de código que contiene la función estática para que sea el mismo que el de la sección que realiza la llamada.

Utilice `DUMPBIN /SYMBOLS` para ver si una función es estática.