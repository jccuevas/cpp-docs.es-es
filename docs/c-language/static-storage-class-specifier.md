---
title: static (Especificador de clase de almacenamiento)
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: 2596e257ae6e22e207451b97b0361aecdfffba03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594043"
---
# <a name="static-storage-class-specifier"></a>static (Especificador de clase de almacenamiento)

Una variable declarada en el nivel interno con el especificador de clase de almacenamiento **static** tiene una duración global pero solo es visible dentro del bloque en el que se declara. Para las cadenas constantes, el uso de **static** es útil porque palía la sobrecarga de inicialización frecuente en funciones invocadas con frecuencia.

## <a name="remarks"></a>Comentarios

Si no se inicializa explícitamente una variable **static**, se inicializa en 0 de forma predeterminada. Dentro de una función, **static** hace que el almacenamiento se asigne y actúa como una definición. Las variables estáticas internas proporcionan almacenamiento permanente privado que es visible solamente a una única función.

## <a name="see-also"></a>Vea también

[Clases de almacenamiento de C](c-storage-classes.md)<br/>
[Clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md)