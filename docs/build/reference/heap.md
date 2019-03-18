---
title: /HEAP
ms.date: 11/04/2016
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: fcf557b467ba5bd04352ba2f2702659a1eb2948d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810359"
---
# <a name="heap"></a>/HEAP

Establece el tamaño del montón en bytes. Esta opción solo se aplica a los archivos ejecutables.

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>Comentarios

El `reserve` argumento especifica la asignación del montón inicial total de memoria virtual. De forma predeterminada, el tamaño del montón es 1 MB. [Referencia de EDITBIN](editbin-reference.md) se redondea el valor especificado al múltiplo de 4 bytes.

El elemento opcional `commit` argumento está sujeto a interpretación por el sistema operativo. En un sistema operativo Windows, especifica la cantidad de memoria física para asignar inicial y la cantidad de memoria adicional para asignar cuando se debe expandir el montón. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Una mayor `commit` valor permite que el sistema asignar memoria menor a menudo, cuando la aplicación necesite más espacio del montón, pero aumentarán los requisitos de memoria y, posiblemente, la duración de inicio de la aplicación. El `commit` valor debe ser menor o igual que el `reserve` valor.

Especifique el `reserve` y `commit` valores en formato decimal o en notación octal o hexadecimal del lenguaje c. Por ejemplo, puede especificarse un valor de 1 MB como 1048576 en decimal, como 0 x 100000 en formato hexadecimal o como 04000000 en octal.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
