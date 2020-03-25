---
title: Advertencia de las herramientas del vinculador LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 4488539a4f7282180048f1e3530e62e35c3b339e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183103"
---
# <a name="linker-tools-warning-lnk4219"></a>Advertencia de las herramientas del vinculador LNK4219

desbordamiento de corrección de nombre de corrección. El destino ' Target Symbol name ' está fuera del intervalo e inserta código thunk

El enlazador insertó un código thunk en una situación en la que la dirección o el desplazamiento no caben en la instrucción dada porque el símbolo de destino está demasiado lejos de la ubicación de la instrucción.

Puede que desee reordenar la imagen (por ejemplo, mediante la opción [/Order](../../build/reference/order-put-functions-in-order.md) ) para evitar el nivel de direccionamiento indirecto adicional.
