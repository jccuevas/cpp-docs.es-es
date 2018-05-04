---
title: Información general sobre x64 convenciones de llamada | Documentos de Microsoft
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
ms.openlocfilehash: eb4071cd3223ad2ab073f84418e641b515c05112
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-x64-calling-conventions"></a>Información general sobre las convenciones de llamada x64
Dos diferencias importantes entre x86 y [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] son la capacidad de direccionamiento de 64 bits y un conjunto simple de 64 bits de 16 registros de uso general. Dado el registros ampliado conjunto, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] utiliza la [__fastcall](../cpp/fastcall.md) convención de llamada y un modelo de control de excepciones basado en RISC. El `__fastcall` convención usa registros para los cuatro primeros argumentos y el marco de pila para pasar argumentos adicionales.  
  
 La opción del compilador siguiente ayuda a optimizar la aplicación para [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/favor (Optimizar para valores específicos de la arquitectura)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>Convención de llamada  
 El [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] interfaz binaria de aplicaciones (ABI) usa una cuatro registro fast convención de llamada de forma predeterminada. Se asigna espacio en la pila de llamadas como un almacén de instantáneas para los destinatarios guardar los registros. Hay una correspondencia estricta entre los argumentos de una llamada de función y los registros que se usa para los argumentos. Cualquier argumento que no cabe en 8 bytes, o no es 1, 2, 4 o 8 bytes, debe pasarse por referencia. No hay ningún intento para distribuir un único argumento en varios registros. X87 pila del registro no se utiliza. Puede utilizarse el destinatario de la llamada, pero debe considerarse volátil en las llamadas a funciones. Punto flotante de todas las operaciones se realizan utilizando los 16 registros de XMM. Argumentos de entero se pasan en registros RCX, RDX, R8 y R9. Argumentos se pasan en XMM0L, XMM1L, XMM2L y XMM3L de punto flotante. argumentos de 16 bytes se pasan por referencia. Paso de parámetros se describen en detalle en [pasando el parámetro](../build/parameter-passing.md). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. Todos los demás registros son no volátiles. Uso de registros está documentada en detalle en [registrar el uso del](../build/register-usage.md) y [guardan registra llamador/destinatario](../build/caller-callee-saved-registers.md).  
  
 El llamador es responsable de asignar espacio para los parámetros para el destinatario y siempre debe asignar espacio suficiente para almacenar los cuatro parámetros de registro, incluso si el destinatario no toma parámetros esa cantidad. Esto simplifica la compatibilidad con funciones de lenguaje C sin prototipo y funciones de C o C++ vararg. Para las funciones vararg o sin prototipo, cualquier punto flotante valores debe duplicarse en el registro de uso general correspondiente. Los parámetros más allá de los primeros cuatro deben almacenarse en la pila, por encima de la tienda de sombra para los primeros cuatro, antes de la llamada. Detalles de la función vararg pueden encontrarse en [Varargs](../build/varargs.md). Información de la función sin prototipo se detalla en [funciones sin prototipo](../build/unprototyped-functions.md).  
  
## <a name="alignment"></a>Alineación  
 Mayoría de las estructuras se alinea según su alineación natural. Las excepciones principales son el puntero de pila y `malloc` o `alloca` memoria, lo que se alinean a 16 bytes con el fin de ayudar al rendimiento. La alineación por encima de 16 bytes debe realizarse manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones de registros de XMM, esto debería funcionar para la mayoría del código. Para obtener más información sobre el diseño de la estructura y la alineación vea [tipos y almacenamiento](../build/types-and-storage.md). Para obtener información sobre el diseño de la pila, vea [uso de la pila](../build/stack-usage.md).  
  
## <a name="unwindability"></a>Capacidad de desenredar  
 Las funciones de hoja son funciones que no cambian los registros no volátiles. Una función no hoja puede cambiar RSP no volátil, por ejemplo, mediante una llamada a una función o la asignación de espacio de pila adicional para las variables locales. Para poder recuperar los registros no volátiles cuando se controla una excepción, las funciones de hoja no se deben anotar con datos estáticos que explica cómo desenredar correctamente la función en una instrucción de arbitraria. Estos datos se almacenan como *pdata*, o datos de procedimiento, que a su vez, hace referencia a *xdata*, los datos de control de excepciones. Lo xdata contiene la información de desenredo y puede apuntar a pdata adicional o una función de controlador de excepción. Los prólogos y epílogos están muy restringida para que se pueden describir correctamente en xdata. El puntero de pila se debe alinear a 16 bytes en cualquier región de código que no forma parte de un epílogo ni un prólogo, excepto en las funciones de hoja. Las funciones de hoja se pueden desenredas simplemente simulando una devolución, por lo que pdata y xdata no son necesarios. Para obtener más información acerca de la estructura adecuada de los de función prólogos y epílogos, consulte [prólogo y epílogo](../build/prolog-and-epilog.md). Para obtener más información sobre el control de excepciones y el control de excepciones y desenredo de pdata y xdata, vea [(x64) de control de excepciones](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)