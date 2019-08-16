---
title: Error del compilador C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328658"
---
# <a name="compiler-error-c3445"></a>Error del compilador C3445

> lista de inicialización de copia de '*tipo*' no se puede usar un constructor explícito

Según la norma ISO C ++ 17 estándar, el compilador es necesario tener en cuenta un constructor explícito para la resolución de sobrecarga de inicialización de la lista de copia, pero debe generar un error si se elige realmente esa sobrecarga.

A partir de Visual Studio 2017, el compilador no encuentra errores relacionados con la creación de objetos mediante el uso de una lista de inicializadores que no se encontraron con Visual Studio 2015. Estos errores podrían provocar bloqueos o un comportamiento indefinido en tiempo de ejecución.

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

Para corregir el error, use en su lugar la inicialización directa:

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
