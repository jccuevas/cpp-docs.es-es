---
title: uso de la pila x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 3318a3512f83e242496454ffa2dc4aa8d26e1fc3
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627324"
---
# <a name="x64-stack-usage"></a>uso de la pila x64

Toda la memoria más allá de la dirección actual de RSP se considera volátil: El sistema operativo o un depurador, puede sobrescribir esta memoria durante una sesión de depuración de usuario o un controlador de interrupción. Por lo tanto, se debe establecer siempre RSP antes de intentar leer o escribir valores en un marco de pila.

En esta sección se explica la asignación de espacio de pila para las variables locales y la **alloca** intrínseco.

## <a name="stack-allocation"></a>Asignación de pila

Prólogo de una función es responsable de asignar espacio de pila para las variables locales, registros guardados, los parámetros de la pila y parámetros de registro.

Siempre es el área de parámetros en la parte inferior de la pila (incluso si `alloca` se usa), de modo que siempre estará adyacente a la dirección de retorno durante cualquier llamada de función. Contiene al menos cuatro entradas, pero siempre espacio suficiente para contener todos los parámetros necesarios para cualquier función que se puede llamar. Tenga en cuenta que siempre se asigna espacio para los parámetros de registro, incluso si los parámetros propios nunca se hospedan en la pila; un destinatario se garantiza que se ha asignado espacio para todos sus parámetros. Direcciones particulares son necesarias para los argumentos del registro para que esté disponible un área contigua en caso de que la función llamada debe tomar la dirección de la lista de argumentos (va_list) o un argumento concreto. Esta área también proporciona un lugar conveniente para guardar los argumentos de registro durante la ejecución de código thunk y como opción de depuración (por ejemplo, hace que los argumentos fáciles de encontrar durante la depuración si están almacenados en sus direcciones de inicio en el código de prólogo). Incluso si la función llamada tiene menos de 4 parámetros, estas ubicaciones de 4 pila eficazmente pertenecen a la función llamada y se pueden usar la función llamada para otros fines además de guardar los valores de registro de parámetro.  Por lo tanto el llamador no puede guardar información en esta región de pila a través de una llamada de función.

Si el espacio se asigna dinámicamente (`alloca`) en una función, a continuación, un registro no volátil debe usarse como un puntero de marco para marcar la base de la parte fija de la pila y que debe guardarse e inicializado en el prólogo de registro. Tenga en cuenta que, cuando `alloca` es utilizado, las llamadas al mismo destinatario desde el mismo llamador pueden tener diferentes direcciones particulares para sus parámetros de registro.

La pila siempre se mantendrá 16 bytes alineados, excepto en el prólogo (por ejemplo, una vez que se inserta el remite) y, excepto donde se indica en [tipos de función](#function-types) para una clase determinada de las funciones de marco.

El siguiente es un ejemplo del diseño de pila donde llamadas de función A una hoja no funcionan prólogo de la función B. la ya ha asignado espacio para todos los parámetros de registro y de pila requeridos por B en la parte inferior de la pila. La llamada inserta el remite y prólogo de B asigna espacio para sus variables locales, los registros no volátiles y el espacio necesario para que pueda llamar a funciones. Si usa B `alloca`, se asigna el espacio entre el registro permanente o variable local área de almacenamiento y el área de la pila de parámetro.

![Ejemplo de conversión de AMD](../build/media/vcamd_conv_ex_5.png "ejemplo de conversión de AMD")

Cuando la función B llama a otra función, se inserta el remite justo debajo de la dirección particular para RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Construcción del área de pila parámetro dinámico

Si se usa un puntero de marco, existe la opción para crear dinámicamente el área de la pila de parámetro. Esto no se realiza actualmente en el x64 compilador.

## <a name="function-types"></a>Tipos de función

Básicamente hay dos tipos de funciones. Se llama a una función que requiere un marco de pila un *enmarcar la función*. Se llama a una función que no requiere un marco de pila un *hoja función*.

Una función de marco es una función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones. También requiere una entrada de la tabla de función. Una función de marco requiere un prólogo y un epílogo. Una función de marco puede asignar dinámicamente el espacio de pila y puede emplear un puntero de marco. Una función de marco tiene todas las capacidades de este estándar de llamada a su disposición.

Si una función de marco no llama a otra función, no es necesario para alinear la pila (al que hace referencia en la sección [asignación de pila](#stack-allocation)).

Una función de hoja es aquella que no requiere una entrada de la tabla de función. No puede realizar cambios en los registros no volátiles, incluidos RSP, lo que significa que no se puede llamar a las funciones o asignar espacio de pila. Puede dejar la pila sin alinear mientras ejecuta.

## <a name="malloc-alignment"></a>alineación de malloc

[malloc](../c-runtime-library/reference/malloc.md) garantiza que devuelven memoria que se alinee correctamente para almacenar cualquier objeto que tiene una alineación fundamental y que podría ajustarse a la cantidad de memoria que se asigna. Un *alineación fundamental* es una alineación que es menor o igual que la alineación mayor que sea compatible con la implementación sin una especificación de alineación. (En Visual C++, esta es la alineación necesaria para un `double`, u 8 bytes. En el código destinado a las plataformas de 64 bits, son 16 bytes). Por ejemplo, una asignación de cuatro bytes se alinearía en un límite que admite cualquier objeto de cuatro bytes o menos.

Visual C++ permite tipos que tienen *alineación extendida*, que son también se denomina *demasiado alineados* tipos. Por ejemplo, los tipos SSE [__m128](../cpp/m128.md) y `__m256`y los tipos que se declaran mediante `__declspec(align( n ))` donde `n` es mayor que 8, tienen alineación extendida. Alineación de memoria en un límite que es adecuado para un objeto que requiere alineación extendida no está garantizada por `malloc`. Para asignar memoria para los tipos demasiado alineados, utilice [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) y funciones relacionadas.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) debe ser 16 bytes que se alinea y además debe usar un puntero de marco.

La pila que se asigna debe incluir el espacio después de él para parámetros de funciones llamadas posteriormente, como se describe en [asignación de pila](#stack-allocation).

## <a name="see-also"></a>Vea también

[x64 convenciones de software](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)