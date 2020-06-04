---
title: Punteros (C++)
ms.date: 11/19/2019
description: Acerca de los punteros sin procesar y los punteros inteligentes en Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371915"
---
# <a name="pointers-c"></a>Punteros (C++)

Un puntero es una variable que almacena la dirección de memoria de un objeto. Los punteros se utilizan ampliamente en C y C++ para tres propósitos principales:

- para asignar nuevos objetos en el montón,
- para pasar funciones a otras funciones
- para iterar elementos en matrices u otras estructuras de datos.

En la programación de estilo C, los *punteros sin procesar* se utilizan para todos estos escenarios. Sin embargo, los punteros sin procesar son el origen de muchos errores de programación graves. Por lo tanto, se desaconseja encarecidamente su uso, excepto cuando proporcionan un beneficio de rendimiento significativo y no hay ambiguedad en cuanto a qué puntero es el *puntero propietario* que es responsable de eliminar el objeto. C++ moderno proporciona punteros inteligentes para asignar *objetos,* *iteradores* para recorrer estructuras de datos y *expresiones lambda* para pasar funciones. Mediante el uso de estos lenguajes y las instalaciones de biblioteca en lugar de punteros sin procesar, hará que su programa sea más seguro, más fácil de depurar y más sencillo de entender y mantener. Consulte [Punteros inteligentes](smart-pointers-modern-cpp.md), [Iteradores](../standard-library/iterators.md)y [expresiones de Lambda](lambda-expressions-in-cpp.md) para obtener más información.

## <a name="in-this-section"></a>En esta sección

- [Punteros básicos](raw-pointers.md)
- [Punteros const y volátiles](const-and-volatile-pointers.md)
- [nuevos y eliminar operadores](new-and-delete-operators.md)
- [Punteros inteligentes](smart-pointers-modern-cpp.md)
- [Cómo: Crear y utilizar instancias de unique_ptr](how-to-create-and-use-unique-ptr-instances.md)
- [Cómo: Crear y utilizar instancias de shared_ptr](how-to-create-and-use-shared-ptr-instances.md)
- [Cómo: Crear y utilizar instancias weak_ptr](how-to-create-and-use-weak-ptr-instances.md)
- [Cómo: Crear y utilizar instancias de CComPtr y CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Consulte también

[Iterators](../standard-library/iterators.md)</br>
[Expresiones lambda](lambda-expressions-in-cpp.md)
