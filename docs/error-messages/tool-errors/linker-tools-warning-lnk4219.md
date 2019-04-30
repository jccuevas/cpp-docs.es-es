---
title: Advertencia de las herramientas del vinculador LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410257"
---
# <a name="linker-tools-warning-lnk4219"></a>Advertencia de las herramientas del vinculador LNK4219

desbordamiento de corrección de nombre de la corrección. 'Nombre de símbolo de destino' de destino está fuera del intervalo, se insertará código thunk

El vinculador inserta un código thunk en una situación donde la dirección o desplazamiento no pudo ajustar en la instrucción dada porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.

Que es posible que desee reordenar la imagen (mediante el [/Order](../../build/reference/order-put-functions-in-order.md) opción, por ejemplo) para evitar el nivel adicional de direccionamiento indirecto.