---
title: Procedimiento para desenredar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 294353baf8c15818ba836bd3093226a78aa6e44c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700666"
---
# <a name="unwind-procedure"></a>Procedimiento para desenredar

La matriz de códigos de desenredado se ordena en orden descendente. Cuando se produce una excepción, se almacena el contexto completo por el sistema operativo en un registro de contexto. A continuación, se invoca la lógica de envío de excepción, que ejecuta repetidamente los pasos siguientes para encontrar un controlador de excepciones.

1. Utilice el RIP actual almacenado en el registro de contexto para buscar una entrada de tabla RUNTIME_FUNCTION que describe la función actual (o parte de la función, en el caso de entradas UNWIND_INFO encadenadas).

1. Si se encuentra ninguna entrada de tabla de función, a continuación, se encuentra en una función de hoja y RSP dirigirá directamente el puntero devuelto. El puntero de devolución en [RSP] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y se repite el paso 1.

1. Si se encuentra una entrada de la tabla de función, RIP puede estar en tres regiones) en un epílogo, (b) en el prólogo o (c) en el código que puede quedar oculto por un controlador de excepciones.

   - Distingue un) si el RIP es dentro de un epílogo, a continuación, control está abandonando la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del epílogo deben continuar para calcular el contexto de la función de llamador. Se examina determinar si el valor de RIP es dentro de un epílogo, la secuencia de código de RIP en. Si ese flujo de código puede coincidir con la parte final de un epílogo legítimo, entonces está en un epílogo y se simula la parte restante del epílogo, con el registro de contexto actualizado como cada instrucción se procesa. Una vez hecho esto, se repite el paso 1.

   - Caso b) si el valor de RIP está en el prólogo, control no ha había entrado en la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del prólogo se deben deshacer para calcular el contexto de la función de llamador. El valor de RIP está en el prólogo si la distancia desde el principio de la función a RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredo. Los efectos del prólogo se desenreda mediante exploración hacia delante a través de la matriz de códigos de desenredo para la primera entrada con un desplazamiento menor o igual que el desplazamiento de RIP desde el principio de la función y, después, deshaciendo el efecto de todos los elementos restantes de la matriz de códigos de desenredado. A continuación, se repite el paso 1.

   - Caso c) si el RIP no está dentro de un prólogo o epílogo y la función tiene un controlador de excepciones (UNW_FLAG_EHANDLER está establecido), entonces se llama controlador específico del lenguaje. El controlador examina sus datos y llamadas a funciones filtro según corresponda. Puede devolver el controlador específico del lenguaje que se ha controlado la excepción o que es la búsqueda debe continuar. También puede iniciar una operación de desenredo directamente.

1. Si el controlador específico del lenguaje devuelve un estado controlado, entonces se puede continuar la ejecución mediante el registro de contexto original.

1. Si no hay ningún controlador específico del lenguaje o el controlador devuelve un estado de "continuar la búsqueda", el registro de contexto debe ser desenredar en el estado del llamador. Esto se logra mediante el procesamiento de todos los elementos de matriz de código de desenredado, deshaciendo el efecto de cada uno. A continuación, se repite el paso 1.

Cuando se encadena desenredo info está relacionado, se siguen estos pasos básicos. La única diferencia es, mientras que recorrer la matriz de códigos de desenredo para desenredar los efectos del prólogo, una vez que se alcanza el final de la matriz, está vinculado a la información de desenredo principal y se recorre la matriz de códigos de desenredado completa que se encuentran allí. Esta vinculación continúa hasta que llegan a una información de desenredo sin el indicador UNW_CHAINED_INFO y termina de recorrer su matriz de códigos de desenredado.

El conjunto más pequeño de datos de desenredo es de 8 bytes. Esto representaría una función que sólo asignó 128 bytes de pila o menos y, posiblemente, se había guarda un registro no volátil. Esto también es el tamaño de un encadenadas desenredo de la estructura de información para un prólogo de longitud cero sin códigos de desenredado.

## <a name="see-also"></a>Vea también

[Control de excepciones (x64)](../build/exception-handling-x64.md)