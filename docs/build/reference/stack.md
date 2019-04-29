---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 6f30877800d4597054601f7459df88c78193fd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318503"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Comentarios

Esta opción establece el tamaño de la pila en bytes y toma argumentos en notación decimal o de lenguaje C. La opción /STACK sólo se aplica a un archivo ejecutable.

El *reservar* argumento especifica la asignación total de la pila de memoria virtual. EDITBIN se redondea el valor especificado a los 4 bytes más cercanos.

El elemento opcional `commit` argumento está sujeto a interpretación por el sistema operativo. En Windows NT, Windows 95 y Windows 98, `commit` especifica la cantidad de memoria física para asignar a la vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Una mayor `commit` valor, ahorrará tiempo cuando la aplicación necesita más espacio de pila, pero aumenta los requisitos de memoria y, posiblemente, el tiempo de inicio.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
