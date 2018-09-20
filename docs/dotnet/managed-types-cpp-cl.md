---
title: Tipos (C++ / CL) administrados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408048"
---
# <a name="managed-types-ccl"></a>Tipos administrados (C++/CL)

La sintaxis de la declaración de tipos administrados y la creación y uso de objetos de estos tipos se ha modificado considerablemente desde extensiones administradas para C++ a Visual C++. Esto se hizo para promover su integración en el sistema de tipos de ISO-C++. Estos cambios se presentan en detalle en las subsecciones siguientes.

## <a name="in-this-section"></a>En esta sección

[Declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)<br/>
Describe cómo declarar un administrado `class`, `struct`, o `interface`.

[Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
Describe cómo declarar un objeto de tipo de clase de referencia mediante un controlador de seguimiento.

[Declaración de una matriz de CLR](../dotnet/declaration-of-a-clr-array.md)<br/>
Explica cómo declarar e inicializar una matriz.

[Cambios en el orden de inicialización de constructores](../dotnet/changes-in-constructor-initialization-order.md)<br/>
Analiza los cambios clave en el orden de inicialización de constructores de clase.

[Cambios en la semántica de los destructores](../dotnet/changes-in-destructor-semantics.md)<br/>
Describe la finalización no determinista, `Finalize` frente a `Dispose`, consecuencias para los objetos de referencia y el uso explícito `Finalize`.

**Nota:** la explicación de los delegados se aplaza hasta que [delegados y eventos](../dotnet/delegates-and-events.md) con el fin de presentar los miembros de evento dentro de una clase, el tema general de [declaraciones de miembros en una clase o interfaz (C++ / C++ / CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>Vea también

[Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Matrices](../windows/arrays-cpp-component-extensions.md)