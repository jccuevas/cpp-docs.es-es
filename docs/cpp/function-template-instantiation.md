---
title: Crear instancias de plantillas de función
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: 6917448af067542fffb13aa043720bf8a26f7ba3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179762"
---
# <a name="function-template-instantiation"></a>Crear instancias de plantillas de función

Cuando se llama por primera vez a una plantilla de función para cada tipo, el compilador genera una creación de instancias. Cada creación de instancias es una versión de la función con plantilla especializada para el tipo concreto. Se llamará a esta creación de instancias cada vez que se use la función para el tipo. Si tiene varias creaciones de instancias idénticas, incluso en módulos diferentes, solo una copia de la creación de instancias terminará agregándose al archivo ejecutable.

La conversión de argumentos de función se permite en las plantillas de función de cualquier par de argumento y parámetro en el que el parámetro no dependa de un argumento de plantilla.

Se pueden crear explícitamente instancias de las plantillas de función si la plantilla se declara con un tipo concreto como argumento. Por ejemplo, se permite el código siguiente:

```cpp
// function_template_instantiation.cpp
template<class T> void f(T) { }

// Instantiate f with the explicitly specified template.
// argument 'int'
//
template void f<int> (int);

// Instantiate f with the deduced template argument 'char'.
template void f(char);
int main()
{
}
```

## <a name="see-also"></a>Consulte también

[Plantillas de función](../cpp/function-templates.md)
