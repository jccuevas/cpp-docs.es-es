---
title: Uso de las pilas x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b598c33fbdd56630ca3e5ef0da551f38a73baa26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335530"
---
# <a name="x64-stack-usage"></a>Uso de las pilas x64

Toda la memoria más allá de la dirección actual de RSP se considera volátil: el sistema operativo, o un depurador, puede sobrescribir esta memoria durante una sesión de depuración de usuario o un controlador de interrupción. Por lo tanto, RSP siempre debe establecerse antes de intentar leer o escribir valores en un marco de pila.

En esta sección se describe la asignación de espacio de pila para variables locales y la **alloca** intrínseca.

## <a name="stack-allocation"></a>Asignación de espacio de pila

El prólogo de una función es responsable de asignar espacio de pila para variables locales, registros guardados, parámetros de pila y parámetros de registro.

El área de parámetro siempre está en `alloca` la parte inferior de la pila (incluso si se utiliza), por lo que siempre será adyacente a la dirección de retorno durante cualquier llamada de función. Contiene al menos cuatro entradas, pero siempre suficiente espacio para contener todos los parámetros necesarios para cualquier función a la que se pueda llamar. Tenga en cuenta que el espacio siempre se asigna para los parámetros de registro, incluso si los propios parámetros nunca se homean en la pila; se garantiza que se ha asignado un destinatario de todos sus parámetros. Las direcciones de inicio son necesarias para los argumentos de registro, por lo que hay un área contigua disponible en caso de que la función llamada necesite tomar la dirección de la lista de argumentos (va_list) o un argumento individual. Esta área también proporciona un lugar conveniente para guardar argumentos de registro durante la ejecución thunk y como una opción de depuración (por ejemplo, hace que los argumentos sean fáciles de encontrar durante la depuración si se almacenan en sus direcciones de inicio en el código de prólogo). Incluso si la función llamada tiene menos de 4 parámetros, estas 4 ubicaciones de pila son efectivamente propiedad de la función llamada y pueden ser utilizadas por la función llamada para otros fines además de guardar los valores de registro de parámetros.  Por lo tanto, el autor de la llamada no puede guardar información en esta región de pila a través de una llamada de función.

Si el espacio se`alloca`asigna dinámicamente ( ) en una función, se debe utilizar un registro no volátil como puntero de marco para marcar la base de la parte fija de la pila y ese registro debe guardarse e inicializarse en el prólogo. Tenga en `alloca` cuenta que cuando se utiliza, las llamadas al mismo destinatario desde el mismo autor de la llamada pueden tener direcciones de inicio diferentes para sus parámetros de registro.

La pila siempre se mantendrá alineada de 16 bytes, excepto dentro del prólogo (por ejemplo, después de insertar la dirección de retorno) y excepto donde se indica en Tipos de [función](#function-types) para una determinada clase de funciones de marco.

A continuación se muestra un ejemplo del diseño de pila donde la función A llama a una función no hoja B. El prólogo de la función A ya ha asignado espacio para todos los parámetros de registro y pila requeridos por B en la parte inferior de la pila. La llamada inserta la dirección de retorno y el prólogo de B asigna espacio para sus variables locales, registros no volátiles y el espacio necesario para que llame a funciones. Si B `alloca`utiliza , el espacio se asigna entre el área de guardado de registro local/no volátil y el área de pila de parámetros.

![Ejemplo de conversión AMD](../build/media/vcamd_conv_ex_5.png "Ejemplo de conversión AMD")

Cuando la función B llama a otra función, la dirección de retorno se inserta justo debajo de la dirección de inicio de RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Construcción dinámica del área de pila de parámetros

Si se utiliza un puntero de marco, existe la opción para crear dinámicamente el área de pila de parámetros. Esto no se hace actualmente en el compilador x64.

## <a name="function-types"></a>Tipos de función

Básicamente hay dos tipos de funciones. Una función que requiere un marco de pila se denomina función de *marco.* Una función que no requiere un marco de pila se denomina *función hoja.*

Una función de marco es una función que asigna espacio de pila, llama a otras funciones, guarda registros no volátiles o utiliza el control de excepciones. También requiere una entrada de tabla de funciones. Una función de marco requiere un prólogo y un epílogo. Una función de marco puede asignar dinámicamente espacio de pila y puede emplear un puntero de marco. Una función de trama tiene a su disposición todas las capacidades de este estándar de llamada.

Si una función de marco no llama a otra función, no es necesario alinear la pila (referenciada en [Asignación](#stack-allocation)de pila de sección ).

Una función hoja es una que no requiere una entrada de tabla de funciones. No puede realizar cambios en ningún registro no volátil, incluido RSP, lo que significa que no puede llamar a ninguna función ni asignar espacio de pila. Se permite dejar la pila sin alinear mientras se ejecuta.

## <a name="malloc-alignment"></a>alineación malloc

[malloc](../c-runtime-library/reference/malloc.md) está garantizado para devolver la memoria que está adecuadamente alineada para almacenar cualquier objeto que tiene una alineación fundamental y que podría caber en la cantidad de memoria que se asigna. Una *alineación fundamental* es una alineación que es menor o igual que la alineación más grande que admite la implementación sin una especificación de alineación. (En Visual C++, esta es la alineación necesaria para un `double`, u 8 bytes. En el código destinado a plataformas de 64 bits, es de 16 bytes.) Por ejemplo, una asignación de cuatro bytes se alinearía en un límite que admita cualquier objeto de cuatro bytes o más pequeño.

Visual C++ permite tipos que tienen *alineación extendida,* que también se conocen como tipos *sobrealineados.* Por ejemplo, los [__m128](../cpp/m128.md) tipos `__m256`de SSE __m128 y `__declspec(align( n ))` `n` , y los tipos que se declaran mediante where es mayor que 8, tienen una alineación extendida. La alineación de memoria en un contorno adecuado para un `malloc`objeto que requiere una alineación extendida no está garantizada por . Para asignar memoria para tipos sobrealineados, utilice [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) y funciones relacionadas.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) debe estar alineado de 16 bytes y, además, utilizar un puntero de marco.

La pila que se asigna debe incluir espacio después de ella para los parámetros de las funciones denominadas posteriormente, como se describe en [Asignación](#stack-allocation)de pila .

## <a name="see-also"></a>Consulte también

[Convenciones de software x64](../build/x64-software-conventions.md)<br/>
[Alinee](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
