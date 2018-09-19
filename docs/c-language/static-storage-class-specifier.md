---
title: static (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1a58a8c7ab6eeb7d304d84cef15beb9046184fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079497"
---
# <a name="static-storage-class-specifier"></a>static (Especificador de clase de almacenamiento)

Una variable declarada en el nivel interno con el especificador de clase de almacenamiento **static** tiene una duración global pero solo es visible dentro del bloque en el que se declara. Para las cadenas constantes, el uso de **static** es útil porque palía la sobrecarga de inicialización frecuente en funciones invocadas con frecuencia.

## <a name="remarks"></a>Comentarios

Si no se inicializa explícitamente una variable **static**, se inicializa en 0 de forma predeterminada. Dentro de una función, **static** hace que el almacenamiento se asigne y actúa como una definición. Las variables estáticas internas proporcionan almacenamiento permanente privado que es visible solamente a una única función.

## <a name="see-also"></a>Vea también

[Clases de almacenamiento de C](c-storage-classes.md)<br/>
[Clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md)