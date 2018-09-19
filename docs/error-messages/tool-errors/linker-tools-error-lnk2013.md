---
title: Las herramientas del vinculador LNK2013 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041745"
---
# <a name="linker-tools-error-lnk2013"></a>Error de las herramientas del vinculador LNK2013

Desbordamiento de la corrección tipo de corrección. 'symbol name' de destino fuera del intervalo

El vinculador no puede ajustar la dirección o desplazamiento requeridos en la instrucción dada, porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.

Puede resolver este problema creando varias imágenes o mediante el [/Order](../../build/reference/order-put-functions-in-order.md) opción para la instrucción y el destino estén más cerca.

Cuando el nombre del símbolo es un símbolo definido por el usuario (y no uno generado por el compilador) también pueden probarse las siguientes acciones para resolver el error:

- Cambiar la función estática para que no sea estática.

- Cambiar el nombre de la sección de código que contiene la función estática para que sea el mismo que el de la sección que realiza la llamada.

Utilice `DUMPBIN /SYMBOLS` para ver si una función es estática.