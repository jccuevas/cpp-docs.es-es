---
title: Referencia de la biblioteca STL/CLR
ms.date: 09/18/2018"
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: 6914b61597e38c94a214089ecc3aeed17aec46d3
ms.sourcegitcommit: 984fb4814a2dd9bcea5ec88c9528707f17a7cffa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51949523"
---
# <a name="stlclr-library-reference"></a>Referencia de la biblioteca STL/CLR

La biblioteca STL/CLR proporciona una interfaz similar a los contenedores de la biblioteca estándar de C++ para su uso con C++ y .NET Framework common language runtime (CLR). STL/CLR es completamente independiente de la implementación de Microsoft de la biblioteca estándar de C++. STL/CLR se mantiene por compatibilidad heredada, pero no se mantiene actualizada con el estándar de C++. Se recomienda encarecidamente usar nativo [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md) contenedores en lugar de STL/CLR siempre que sea posible.

Para utilizar STL/CLR:

- Incluir encabezados de la **cliext** incluyen el subdirectorio en lugar de los equivalentes de la biblioteca estándar de C++ habituales.

- Calificar nombres de biblioteca con `cliext::` en lugar de `std::`.

La biblioteca STL/CLR proporciona una interfaz similar a STL para su uso con C++ y .NET Framework common language runtime (CLR). Esta biblioteca se mantiene por compatibilidad heredada, pero no se mantiene actualizada con el estándar de C++. Se recomienda encarecidamente usar nativo [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md) contenedores en lugar de STL/CLR.

## <a name="in-this-section"></a>En esta sección

[cliext (Espacio de nombres)](../dotnet/cliext-namespace.md)<br/>
Describe el espacio de nombres que contiene todos los tipos de la biblioteca STL/CLR.

[Contenedores de STL/CLR](../dotnet/stl-clr-containers.md)<br/>
Proporciona información general de los contenedores que se encuentran en la biblioteca estándar de C++, incluidos los requisitos para los elementos de contenedor, tipos de elementos que se pueden insertar y problemas de propiedad.

[Requisitos de los elementos contenedores de STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Describe los requisitos mínimos para todos los tipos de referencia que se insertan en contenedores de la biblioteca estándar de C++.

[Cómo: Convertir una colección .NET en un contenedor STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
Describe cómo convertir una colección de .NET en un contenedor de STL/CLR.

[Cómo: Convertir un contenedor STL/CLR en una colección .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
Describe cómo convertir un contenedor STL/CLR en una colección. NET.

[Cómo: Exponer un contenedor de STL/CLR desde un ensamblado](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
Muestra cómo mostrar los elementos de varios contenedores STL/CLR escritos en un ensamblado de C++.

Además, esta sección también describen los siguientes componentes de STL/CLR:

|||
|-|-|
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|

## <a name="see-also"></a>Vea también

[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
