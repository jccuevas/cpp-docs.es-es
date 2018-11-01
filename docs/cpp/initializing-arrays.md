---
title: Inicializar matrices
ms.date: 11/04/2016
helpviewer_keywords:
- initializing arrays [C++]
- arrays [C++], initializing
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
ms.openlocfilehash: e055e7759865fc151176097c6f0afd9ee237f4c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447091"
---
# <a name="initializing-arrays"></a>Inicializar matrices

Si una clase tiene un constructor, las matrices de esa clase las inicializa un constructor. Si hay menos elementos en la lista de inicializadores que en la matriz, se usa el constructor predeterminado para los elementos restantes. Si no se define ningún constructor predeterminado para la clase, la lista de inicializadores debe estar completa (es decir, debe haber un inicializador para cada elemento de la matriz).

Considere la clase `Point`, que define dos constructores:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

El primer elemento de `aPoint` se construye utilizando el constructor `Point( int, int )`; los dos elementos restantes se crean con el constructor predeterminado.

Matrices miembro estático (si **const** o no) se pueden inicializar en sus definiciones (fuera de la declaración de clase). Por ejemplo:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```