---
title: "Informaci&#243;n general sobre las convenciones de llamada x64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Informaci&#243;n general sobre las convenciones de llamada x64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dos modificaciones importantes de x86 a [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] son la capacidad de direccionamiento de 64 bits y un conjunto simple de 16 registros de 64 bits para uso general.  Dado el conjunto de registros ampliado, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] simplemente utiliza la convención de llamada [\_\_fastcall](../cpp/fastcall.md) y un modelo de control de excepciones basado en RISC.  El modelo `__fastcall` usa registros para los primeros cuatro argumentos y el marco de pila para pasar los otros parámetros.  
  
 La opción del compilador siguiente ayuda a optimizar la aplicación para [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [\/favor \(optimizar para valores específicos de la arquitectura\)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## Convención de llamada  
 La ABI \(Application Binary Interface, Interfaz binaria de aplicaciones\) de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] es una convención de llamada rápida de cuatro registros, con seguimiento regresivo de pila para dichos registros.  Hay una correspondencia estricta de uno a uno entre los argumentos de una función y los registros de dichos argumentos.  Cualquier argumento que no se ajuste a 8 bytes, o que no sea de 1, 2, 4 u 8 bytes, se debe pasar por referencia.  No hay ningún intento de expandir un argumento único por varios registros.  No se usa la pila de registro X87.  Se puede utilizar, pero debe considerarse volátil en las llamadas a funciones.  Todas las operaciones de punto flotante se realizan utilizando los 16 registros de XMM.  Los argumentos se pasan en los registros RCX, RDX, R8 y R9.  Si los argumentos son float o double, se pasan en XMM0L, XMM1L, XMM2L y XMM3L.  Los argumentos de 16 bytes se pasan por referencia.  El paso de parámetros se describe en detalle en [Paso de parámetros](../build/parameter-passing.md).  Además de estos registros, RAX, R10, R11, XMM4 y XMM5 son volátiles.  Todos los demás registros son no volátiles.  El uso de registros se documenta en detalle en [Uso de registros](../build/register-usage.md) y [Registros guardados del llamador y del destinatario](../build/caller-callee-saved-registers.md).  
  
 El llamador es el responsable de asignar espacio para parámetros al destinatario, y siempre debe asignar suficiente espacio para los cuatro parámetros de registro, incluso si el destinatario no tiene tantos parámetros.  Esto ayuda en la simplicidad de admitir funciones sin prototipo de C y funciones vararg de C\/C\+\+.  Para las funciones vararg o sin prototipo, cualquier valor flotante se debe duplicar en el registro de uso general correspondiente.  Cualquier parámetro por encima de los cuatro primeros se debe almacenar en la pila, sobre la memoria auxiliar para los primeros cuatro, antes de la llamada.  Se pueden encontrar detalles sobre la función vararg en [Varargs](../build/varargs.md).  Se detalla información sobre la función sin prototipo en [Funciones sin prototipo](../build/unprototyped-functions.md).  
  
## Alineación  
 La mayoría de las estructuras se alinean según su alineación natural.  Las excepciones principales son el puntero de pila y el puntero malloc o alloca memory, que se alinean a 16 bytes, para ayudar al rendimiento.  La alineación por encima de los 16 bytes se debe realizar manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones XMM, debe ser suficiente para la mayor parte del código.  Para obtener más información sobre el diseño de la estructura y la alineación vea [Tipos y almacenamiento](../build/types-and-storage.md).  Para obtener información sobre el diseño de la pila, vea [Uso de las pilas](../build/stack-usage.md).  
  
## Capacidad de desenredar  
 Todas las funciones de hoja \[funciones que no llaman a otra función, ni se asignan espacio de pila\] se deben agregar con los datos \[denominados xdata o ehdata, a los que se señala desde pdata\] que describen al sistema operativo cómo se deben desenredar adecuadamente, para recuperar registros no volátiles.  Los prólogos y epílogos están muy restringidos, para que se puedan describir correctamente en xdata.  El puntero de pila se debe alinear a 16 bytes, excepto para las funciones de hoja, en cualquier región del código que no forme parte de un epílogo ni un prólogo.  Para obtener detalles sobre la estructura apropiada de los prólogos y epílogos de función, vea [Prólogo y epílogo](../build/prolog-and-epilog.md).  Para obtener más información sobre el control de excepciones y el control de excepciones\/desenredo de pdata y xdata, vea [Control de excepciones \(x64\)](../build/exception-handling-x64.md).  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)