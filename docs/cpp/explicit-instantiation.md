---
title: creación de instancias explícita
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: dbe8bebf91a174e07c7c5cce8e9caf1cf3432edf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180035"
---
# <a name="explicit-instantiation"></a>creación de instancias explícita

Puede utilizar la creación de instancias explícita para crear una instancia de una clase o una función con plantilla sin usarla realmente en el código. Como esto es útil cuando se crean archivos de biblioteca (.lib) que utilizan plantillas para la distribución, las definiciones de plantillas sin instancias no se colocan en archivos objeto (.obj).

Este código crea explícitamente instancias de `MyStack` para las variables **int** y seis elementos:

```cpp
template class MyStack<int, 6>;
```

Esta instrucción crea una instancia de `MyStack` sin reservar ningún almacenamiento para un objeto. Se genera el código para todos los miembros.

La línea siguiente crea explícitamente instancias solo de la función miembro de constructor:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Puede crear explícitamente instancias de las plantillas de función mediante un argumento de tipo específico para volver a declararlas, tal como se muestra en el ejemplo de [creación de instancias de plantillas de función](../cpp/function-template-instantiation.md).

Puede usar la palabra clave **extern** para evitar la creación automática de instancias de miembros. Por ejemplo:

```cpp
extern template class MyStack<int, 6>;
```

Del mismo modo, puede marcar determinados miembros como externos y no crear instancias de ellos:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Puede usar la palabra clave **extern** para evitar que el compilador genere el mismo código de creación de instancias en más de un módulo de objeto. Para crear instancias de la función de plantilla se deben utilizar los parámetros de plantilla explícitos especificados en al menos un módulo vinculado si se llama a la función; de lo contrario, se producirá un error del vinculador cuando se compile el programa.

> [!NOTE]
>  La palabra clave **extern** de la especialización solo se aplica a las funciones miembro definidas fuera del cuerpo de la clase. Las funciones definidas dentro de la declaración de clase se consideran funciones insertadas y siempre se crean instancias de ellas.

## <a name="see-also"></a>Consulte también

[Plantillas de función](../cpp/function-templates.md)
