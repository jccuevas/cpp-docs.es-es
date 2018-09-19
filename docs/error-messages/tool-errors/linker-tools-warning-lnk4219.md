---
title: Las herramientas del vinculador LNK4219 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105217"
---
# <a name="linker-tools-warning-lnk4219"></a>Advertencia de las herramientas del vinculador LNK4219

desbordamiento de corrección de nombre de la corrección. 'Nombre de símbolo de destino' de destino está fuera del intervalo, se insertará código thunk

El vinculador inserta un código thunk en una situación donde la dirección o desplazamiento no pudo ajustar en la instrucción dada porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.

Que es posible que desee reordenar la imagen (mediante el [/Order](../../build/reference/order-put-functions-in-order.md) opción, por ejemplo) para evitar el nivel adicional de direccionamiento indirecto.