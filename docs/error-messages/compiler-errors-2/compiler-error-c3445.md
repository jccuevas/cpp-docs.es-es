---
title: C3445 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256771"
---
# <a name="compiler-error-c3445"></a>C3445 de Error del compilador

> lista de inicialización de copia de '*tipo*' no se puede utilizar un constructor explícito

Según el estándar C ++ 17 ISO, el compilador es necesario tener en cuenta un constructor explícito para la resolución de sobrecarga en la inicialización de la lista de copia, pero debe generar un error si se elige esa sobrecarga.

A partir de Visual Studio de 2017, el compilador no encuentra errores relacionados con la creación de objetos mediante el uso de una lista de inicializadores que no se encontraron mediante Visual Studio 2015. Estos errores pudieron provocar errores o un comportamiento indefinido en tiempo de ejecución.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Para corregir el error, utilice en su lugar la inicialización directa:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
