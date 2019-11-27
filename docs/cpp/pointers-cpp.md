---
title: Punteros (C++)
ms.date: 11/19/2019
description: Acerca de los punteros sin formato y los punteros inteligentes en Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246419"
---
# <a name="pointers-c"></a>Punteros (C++)

Un puntero es una variable que almacena la dirección de memoria de un objeto. Los punteros se utilizan exhaustivamente en C y C++ para tres propósitos principales:

- para asignar nuevos objetos en el montón,
- para pasar funciones a otras funciones
- para recorrer en iteración los elementos de matrices u otras estructuras de datos.

En la programación de estilo C, los *punteros sin formato* se utilizan para todos estos escenarios. Sin embargo, los punteros sin formato son el origen de muchos errores de programación graves. Por lo tanto, se desaconseja encarecidamente su uso, excepto cuando proporcionan una ventaja de rendimiento significativa y no hay ninguna ambigüedad en cuanto a qué puntero es el *puntero propietario* que es responsable de eliminar el objeto. Moderno C++ proporciona *punteros inteligentes* para asignar objetos, *iteradores* para atravesar estructuras de datos y *expresiones lambda* para pasar funciones. Mediante el uso de estas funciones de biblioteca y lenguaje en lugar de punteros sin formato, hará que el programa sea más seguro y fácil de depurar, y que sea más fácil de entender y mantener. Vea [punteros inteligentes](smart-pointers-modern-cpp.md), [iteradores](../standard-library/iterators.md)y [expresiones lambda](lambda-expressions-in-cpp.md) para obtener más información.

## <a name="in-this-section"></a>En esta sección

- [Punteros sin formato](raw-pointers.md)
- [Punteros const y volatile](const-and-volatile-pointers.md)
- [operadores New y DELETE](new-and-delete-operators.md)
- [Punteros inteligentes](smart-pointers-modern-cpp.md)
- [Cómo: crear y usar instancias de unique_ptr](how-to-create-and-use-unique-ptr-instances.md)
- [Cómo: crear y usar instancias de shared_ptr](how-to-create-and-use-shared-ptr-instances.md)
- [Cómo: crear y usar instancias de weak_ptr](how-to-create-and-use-weak-ptr-instances.md)
- [Cómo: crear y usar instancias de CComPtr y CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Vea también

[Iteradores](../standard-library/iterators.md)</br>
[Expresiones lambda](lambda-expressions-in-cpp.md)
