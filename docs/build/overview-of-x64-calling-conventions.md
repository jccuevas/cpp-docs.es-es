---
title: Información general de x64 las convenciones de llamada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e70f4017cb31fcc76b1cf3ef2a77d3a28e31bd28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707998"
---
# <a name="overview-of-x64-calling-conventions"></a>Información general sobre las convenciones de llamada x64

Dos diferencias importantes entre x86 y x64 son la capacidad de direccionamiento de 64 bits y un conjunto simple de 64 bits de 16 registros de uso general. Dado el conjunto de registros expandida, x64 usa el [__fastcall](../cpp/fastcall.md) convención de llamada y un modelo de control de excepciones basado en RISC. El `__fastcall` convención usa registros para los cuatro primeros argumentos y el marco de pila para pasar argumentos adicionales.

La opción del compilador siguiente le ayuda a optimizar su aplicación para x64:

- [/favor (Optimizar para valores específicos de la arquitectura)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="calling-convention"></a>Convención de llamada

De forma predeterminada el x64 interfaz binaria de aplicación (ABI) utiliza una convención de llamada de cuatro registro fast llamada por. Se asigna espacio en la pila de llamadas como almacén de instantáneas de destinatarios guardar esos registros. Hay una correspondencia estricta entre los argumentos de una llamada de función y los registros que se usan para los argumentos. Cualquier argumento que no cabe en 8 bytes, o no es 1, 2, 4 u 8 bytes, se debe pasar por referencia. No hay ningún intento para abarcar varios registros en un único argumento. X87 se utiliza la pila del registro. Se puede usar el destinatario, pero debe considerarse volátil en las llamadas de función. Punto flotante de todas las operaciones se realizan utilizando los 16 registros de XMM. Argumentos de entero se pasan en registros RCX, RDX, R8 y R9. Los argumentos se pasan en XMM0L, XMM1L, XMM2L y XMM3L de punto flotante. argumentos de 16 bytes se pasan por referencia. Paso de parámetros se describen en detalle en [pasando el parámetro](../build/parameter-passing.md). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. Todos los demás registros son volátiles. Uso de registros se documenta detalladamente en [registrar uso](../build/register-usage.md) y [guardado registra el llamador y destinatario](../build/caller-callee-saved-registers.md).

El llamador es responsable de asignar espacio para los parámetros para el destinatario y siempre debe asignar espacio suficiente para almacenar los cuatro parámetros de registro, incluso si el destinatario no toma parámetros esa cantidad. Esto simplifica la compatibilidad con funciones de lenguaje C sin prototipo y funciones de C o C++ vararg. Para funciones vararg o sin prototipo, cualquier punto flotante, los valores deben duplicarse en el registro de uso general correspondiente. Los parámetros más allá de los primeros cuatro se deben almacenar en la pila, encima de la tienda de sombra para los primeros cuatro, antes de la llamada. Detalles de la función vararg pueden encontrarse en [Varargs](../build/varargs.md). Información de la función sin prototipo se detalla en [funciones sin prototipo](../build/unprototyped-functions.md).

## <a name="alignment"></a>Alineación

Mayoría de las estructuras se alinea según su alineación natural. Las excepciones principales son el puntero de pila y `malloc` o `alloca` memoria, lo que se alinean a 16 bytes para ayudar al rendimiento. La alineación por encima de 16 bytes que debe realizarse manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones de registros de XMM, esto debería funcionar para la mayoría del código. Para obtener más información sobre el diseño de la estructura y la alineación vea [tipos y almacenamiento](../build/types-and-storage.md). Para obtener información sobre el diseño de pila, vea [uso de la pila](../build/stack-usage.md).

## <a name="unwindability"></a>Capacidad de desenredar

Las funciones de hoja son funciones que no cambian los registros no volátiles. Una función no hoja puede cambiar RSP no volátil, por ejemplo, llamando a una función o asignación de espacio de pila adicional para las variables locales. Con el fin de recuperar los registros no volátiles cuando se controla una excepción, las funciones de hoja no se deben anotar con datos estáticos que se describen cómo la función en una instrucción arbitraria de desenredado correctamente. Estos datos se almacenan como *pdata*, o datos de procedimiento, que a su vez hace referencia a *xdata*, los datos de control de excepciones. Contiene la información de desenredo lo xdata y puede apuntar a pdata adicional o una función de controlador de excepción. Los prólogos y epílogos están muy restringida para que se pueden describir correctamente en xdata. El puntero de pila se alineen con 16 bytes en cualquier región de código que no forma parte de un epílogo ni un prólogo, excepto dentro de las funciones de hoja. Las funciones de hoja se pueden desenredas simplemente simulando una devolución, por lo que no se requieren pdata y xdata. Para obtener más información acerca de la estructura adecuada de la función prólogos y epílogos, consulte [prólogo y epílogo](../build/prolog-and-epilog.md). Para obtener más información sobre el control de excepciones y el control de excepciones y desenredo de pdata y xdata, vea [Exception Handling (x64)](../build/exception-handling-x64.md).

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)