---
title: Uso de las pilas x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 902e4304ac124be46c6edf0860118dc522b34890
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422755"
---
# <a name="x64-stack-usage"></a>Uso de las pilas x64

Toda la memoria más allá de la dirección actual de RSP se considera volátil: el sistema operativo, o un depurador, puede sobrescribir esta memoria durante una sesión de depuración de usuario o un controlador de interrupciones. Por lo tanto, RSP siempre debe establecerse antes de intentar leer o escribir valores en un marco de pila.

En esta sección se describe la asignación de espacio de pila para las variables locales y el intrínseco **alloca** .

## <a name="stack-allocation"></a>Asignación de la pila

El prólogo de una función es responsable de la asignación de espacio de pila para las variables locales, los registros guardados, los parámetros de la pila y los parámetros de registro.

El área de parámetros siempre está en la parte inferior de la pila (aunque se use `alloca`), por lo que siempre será adyacente a la dirección de devolución durante cualquier llamada de función. Contiene al menos cuatro entradas, pero siempre hay espacio suficiente para contener todos los parámetros que necesita cualquier función a la que se pueda llamar. Tenga en cuenta que siempre se asigna espacio para los parámetros de registro, incluso si los propios parámetros nunca se alojan en la pila; un destinatario tiene la garantía de que se ha asignado espacio para todos sus parámetros. Se requieren direcciones de inicio para los argumentos de registro, por lo que hay disponible un área contigua en caso de que la función a la que se llama deba tomar la dirección de la lista de argumentos (va_list) o un argumento individual. Esta área también proporciona un lugar cómodo para guardar los argumentos de registro durante la ejecución del código thunk y como una opción de depuración (por ejemplo, facilita la búsqueda de los argumentos durante la depuración si se almacenan en sus direcciones particulares en el código de prólogo). Incluso si la función a la que se llama tiene menos de 4 parámetros, estas 4 ubicaciones de la pila son propiedad de forma eficaz por la función llamada y se pueden usar con la función llamada para otros fines además de guardar los valores de registro de parámetros.  Por lo tanto, es posible que el llamador no guarde información en esta región de stack a través de una llamada de función.

Si el espacio se asigna dinámicamente (`alloca`) en una función, se debe usar un registro no volátil como puntero de marco para marcar la base de la parte fija de la pila y dicho registro debe guardarse e inicializarse en el prólogo. Tenga en cuenta que cuando se utiliza `alloca`, las llamadas al mismo destinatario del mismo llamador pueden tener direcciones particulares diferentes para sus parámetros de registro.

La pila siempre se mantendrá alineada de 16 bytes, excepto en el prólogo (por ejemplo, después de insertar la dirección de retorno), excepto cuando se indique en los [tipos de función](#function-types) de una determinada clase de funciones de marco.

A continuación se incluye un ejemplo del diseño de pila en el que la función A llama a una función no hoja B. el prólogo de la función A ya ha asignado espacio para todos los parámetros de la pila y el registro requeridos por B en la parte inferior de la pila. La llamada envía la dirección de retorno y el prólogo de B asigna espacio para sus variables locales, registros no volátiles y el espacio necesario para que llame a las funciones. Si B usa `alloca`, el espacio se asigna entre el área de almacenamiento de la variable local/no volátil y el área de la pila de parámetros.

![Ejemplo de conversión de AMD](../build/media/vcamd_conv_ex_5.png "Ejemplo de conversión AMD")

Cuando la función B llama a otra función, la dirección de devolución se inserta justo debajo de la dirección de inicio de RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Construcción del área de pila de parámetros dinámicos

Si se usa un puntero de marco, existe la opción de crear dinámicamente el área de pila de parámetros. Esto no se realiza actualmente en el compilador x64.

## <a name="function-types"></a>Tipos de función

Básicamente, hay dos tipos de funciones. Una función que requiere un marco de pila se denomina *función de marco*. Una función que no requiere un marco de pila se denomina *función de hoja*.

Una función de marco es una función que asigna espacio de pila, llama a otras funciones, guarda registros no volátiles o usa el control de excepciones. También requiere una entrada de la tabla de funciones. Una función de marco requiere un prólogo y un epílogo. Una función de marco puede asignar dinámicamente el espacio de pila y puede emplear un puntero de marco. Una función de marco tiene todas las capacidades de este estándar de llamada a su disposición.

Si una función de marco no llama a otra función, no es necesario alinear la pila (a la que se hace referencia en la asignación de la [pila](#stack-allocation)de la sección).

Una función de hoja es aquella que no requiere una entrada de tabla de función. No puede realizar cambios en los registros no volátiles, incluido RSP, lo que significa que no puede llamar a ninguna función ni asignar espacio de pila. Se permite dejar la pila sin alinear mientras se ejecuta.

## <a name="malloc-alignment"></a>alineación de malloc

se garantiza que [malloc](../c-runtime-library/reference/malloc.md) devuelve memoria que se alinea de forma adecuada para almacenar cualquier objeto que tenga una alineación fundamental y que podría caber en la cantidad de memoria que se asigna. Una *alineación fundamental* es una alineación que es menor o igual que la alineación más grande admitida por la implementación sin una especificación de alineación. (En Visual C++, es la alineación necesaria para un `double`u 8 bytes. En el código que tiene como destino las plataformas de 64 bits, es de 16 bytes). Por ejemplo, una asignación de cuatro bytes se alineará en un límite que admita cualquier objeto de cuatro bytes o más pequeño.

Visual C++ permite tipos que tienen *alineación extendida*, que también se denominan tipos que se *alinean en exceso* . Por ejemplo, los tipos SSE [__m128](../cpp/m128.md) y `__m256`, y los tipos que se declaran mediante `__declspec(align( n ))` donde `n` es mayor que 8, tienen alineación extendida. La alineación de memoria en un límite adecuado para un objeto que requiere alineación extendida no está garantizada por `malloc`. Para asignar memoria para tipos demasiado alineados, use [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) y funciones relacionadas.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) debe tener una alineación de 16 bytes y, además, es necesario usar un puntero de marco.

La pila que se asigna necesita incluir espacio después de ella para los parámetros de las funciones llamadas posteriormente, como se describe en asignación de la [pila](#stack-allocation).

## <a name="see-also"></a>Consulte también

[Convenciones de software x64](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
