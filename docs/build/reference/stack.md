---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438887"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Observaciones

Esta opción establece el tamaño de la pila en bytes y toma argumentos en notación decimal o de lenguaje C. La opción/STACK solo se aplica a un archivo ejecutable.

El argumento *Reserve* especifica la asignación total de la pila en la memoria virtual. EDITBIN redondea el valor especificado a los 4 bytes más cercanos.

El argumento opcional `commit` está sujeto a la interpretación por el sistema operativo. En Windows NT, Windows 95 y Windows 98, `commit` especifica la cantidad de memoria física que se va a asignar a la vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Un valor `commit` mayor ahorra tiempo cuando la aplicación necesita más espacio de pila, pero aumenta los requisitos de memoria y, posiblemente, el tiempo de inicio.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)
