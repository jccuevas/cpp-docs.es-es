---
title: Procedimiento para desenredar | Documentos de Microsoft
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
ms.openlocfilehash: 5e2a5af5d8db5974aa10595bbd3bac1cd032a0f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382028"
---
# <a name="unwind-procedure"></a>Procedimiento para desenredar
La matriz de códigos de desenredado se ordena en orden descendente. Cuando se produce una excepción, se almacena el contexto completo por el sistema operativo en un registro de contexto. A continuación, se invoca la lógica de envío de excepción, que ejecuta varias veces los pasos siguientes para encontrar un controlador de excepciones.  
  
1.  Utilice el valor de RIP actual almacenado en el registro de contexto para buscar una entrada de la tabla RUNTIME_FUNCTION que describe la función actual (o parte de la función, en el caso de entradas UNWIND_INFO encadenadas).  
  
2.  Si no se encuentra ninguna entrada de tabla de la función, a continuación, está en una función de hoja y RSP dirigirá directamente el puntero de devolución. El puntero de devolución en [RSP] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y se repite el paso 1.  
  
3.  Si se encuentra una entrada de la tabla de función, RIP puede estar en tres regiones (a) en un epílogo, b) en el prólogo o c) en el código que puede estar incluido en un controlador de excepciones.  
  
    -   Mayúsculas un) si el valor de RIP está dentro de un epílogo, a continuación, control está abandonando la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del epílogo deben continuar para calcular el contexto de la función de llamador. Para determinar si el valor de RIP está dentro de un epílogo, las secuencias de código de RIP en se examina. Si esa secuencia de código puede coincidir con la parte final de un epílogo legítimo, a continuación, se encuentra en un epílogo y la parte restante del epílogo se simula, con el registro de contexto actualizado como cada instrucción se procesa. Después de esto, se repite el paso 1.  
  
    -   Caso b) si el valor de RIP está en el prólogo, control no ha había entrado en la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del prólogo se deben deshacer para calcular el contexto de la función de llamador. El valor de RIP está en el prólogo si la distancia desde el principio de la función a RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredo. Los efectos del prólogo se desenreda mediante exploración hacia delante por la matriz de códigos de desenredo para la primera entrada con un desplazamiento menor o igual que el desplazamiento de RIP desde el principio de la función, y luego deshaciendo el efecto de todos los elementos restantes en la matriz de códigos de desenredado. A continuación, se repite el paso 1.  
  
    -   Caso c) si el valor de RIP no está dentro de un prólogo o epílogo y la función tiene un controlador de excepciones (UNW_FLAG_EHANDLER está establecido), a continuación, se llama al controlador específico del lenguaje. El controlador examina sus datos y llamadas a funciones filtro según corresponda. Puede devolver el controlador específico del lenguaje que se controló la excepción o que la búsqueda no distingue para continuar. También puede iniciar una operación de desenredo directamente.  
  
4.  Si el controlador específico del lenguaje devuelve un estado controlado, a continuación, continuar la ejecución con el registro de contexto original.  
  
5.  Si no hay ningún controlador específico del lenguaje o el controlador devuelve un estado de "continuar la búsqueda", el registro de contexto debe ser desenredar en el estado del llamador. Esto se logra mediante el procesamiento de todos los elementos de matriz de código de desenredo, deshaciendo el efecto de cada uno. A continuación, se repite el paso 1.  
  
 Cuando se encadena desenredo información está implicada, se siguen estos pasos básicos. La única diferencia es que, al recorrer la matriz de códigos de desenredo para desenredar efectos del prólogo, una vez que se alcanza el final de la matriz,, a continuación, vinculado a la información de desenredo principal y se recorre la matriz de códigos de desenredado todo encuentra allí. Esta vinculación continúa hasta que llegan a una información de desenredo sin el indicador UNW_CHAINED_INFO y termina de recorrer su matriz de códigos de desenredado.  
  
 El conjunto más pequeño de datos de desenredo es de 8 bytes. Esto representaría una función que sólo asignó 128 bytes de pila o menos y que posiblemente guardó un registro no volátil. Esto también es el tamaño de un encadenadas desenredo de la estructura de información para un prólogo de longitud cero con ningún código de desenredado.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones (x64)](../build/exception-handling-x64.md)