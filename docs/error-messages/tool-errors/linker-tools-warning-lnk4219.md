---
title: Las herramientas del vinculador LNK4219 advertencia | Documentos de Microsoft
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
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4219"></a>Advertencia de las herramientas del vinculador LNK4219
desbordamiento de la corrección de nombre de la corrección. 'Nombre de símbolo de destino' de destino está fuera del intervalo, se insertará código thunk  
  
 El vinculador inserta un código thunk en una situación donde la dirección o desplazamiento no pudo caber en la instrucción dada porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.  
  
 Puede que desee reordenar la imagen (usando la [/orden](../../build/reference/order-put-functions-in-order.md) opción, por ejemplo) para evitar el nivel adicional de direccionamiento indirecto.