---
title: Requisitos de los elementos contenedores de STL/CLR
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 113624b15a0c2c6062feb7113c4771fda6d6cf39
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739408"
---
# <a name="requirements-for-stlclr-container-elements"></a>Requisitos de los elementos contenedores de STL/CLR

Todos los tipos de referencia que se insertan en contenedores STL/CLR deben tener, como mínimo, los siguientes elementos:

- Un constructor de copia público.

- Un operador de asignación pública.

- Un destructor público.

Además, los contenedores asociativos como [establecer](../dotnet/set-stl-clr.md) y [mapa](../dotnet/map-stl-clr.md) debe tener un operador de comparación público definido, que es `operator<` de forma predeterminada. Algunas operaciones en los contenedores también podrían requerir un constructor público predeterminado y que se defina un operador de equivalencia público.

Al igual que los tipos de referencia, los tipos de valor y los identificadores para hacer referencia a tipos que se va a insertar en un contenedor asociativo deben tener un operador de comparación como `operator<` definido. Los requisitos para un constructor de copia público, operador de asignación pública y un destructor público no existen para que tipos de valor o identificadores a tipos de referencia.

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
