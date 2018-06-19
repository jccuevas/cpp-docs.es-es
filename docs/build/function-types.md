---
title: Tipos de función | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322bd45abbfe217671fd39f0617987fde21445db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367656"
---
# <a name="function-types"></a>Tipos de funciones
Básicamente hay dos tipos de funciones. Una función que requiere un marco de pila se llama una función de marco. Una función que no requiere un marco de pila se llamó a una función de hoja.  
  
 Una función de marco es una función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones. También requiere una entrada de tabla de la función. Una función de marco requiere un prólogo y un epílogo. Una función de marco puede asignar dinámicamente el espacio de pila y puede emplear un puntero de marco. Una función de marco tiene todas las capacidades de este estándar de llamada a su disposición.  
  
 Si una función de marco no llama a otra función, no es necesario para alinear la pila (al que hace referencia en la sección [asignación de la pila](../build/stack-allocation.md)).  
  
 Una función de hoja es aquella que no requiere una entrada de tabla de la función. No puede realizar cambios en los registros no volátiles, incluidos RSP, lo que significa que no se puede llamar a las funciones o asignar espacio de pila. Se permite dejar sin alinear la pila mientras ejecuta.  
  
## <a name="see-also"></a>Vea también  
 [Uso de las pilas](../build/stack-usage.md)
