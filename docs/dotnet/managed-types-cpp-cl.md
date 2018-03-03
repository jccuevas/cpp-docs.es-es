---
title: Tipos (C++ CL) administrados | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e7bbd9687c3cc696b35e0284d55a18f59c898cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="managed-types-ccl"></a>Tipos administrados (C++/CL)
La sintaxis de la declaración de tipos administrados y la creación y uso de objetos de estos tipos se ha alterado significativamente desde extensiones administradas para C++ a Visual C++. Esto se hacía para promover su integración en el sistema de tipos de ISO C++. Estos cambios se presentan en detalle en las subsecciones siguientes.  
  
## <a name="in-this-section"></a>En esta sección  
 [Declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)  
 Describe cómo declarar un administrado `class`, `struct`, o `interface`.  
  
 [Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 Describe cómo declarar un objeto de tipo de clase de referencia mediante un identificador de seguimiento.  
  
 [Declaración de una matriz de CLR](../dotnet/declaration-of-a-clr-array.md)  
 Explica cómo declarar e inicializar una matriz.  
  
 [Cambios en el orden de inicialización de constructores](../dotnet/changes-in-constructor-initialization-order.md)  
 Analiza los cambios clave en el orden de inicialización del constructor de clase.  
  
 [Cambios en la semántica de los destructores](../dotnet/changes-in-destructor-semantics.md)  
 Describe la finalización no determinista, `Finalize` frente a `Dispose`, ramificaciones para los objetos de referencia y el uso explícito `Finalize`.  
  
 **Nota:** la explicación de los delegados se retrasa hasta el [delegados y eventos](../dotnet/delegates-and-events.md) para presentarlos con miembros de evento dentro de una clase, el tema general de [declaraciones de miembros en una clase o interfaz (C++ / CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## <a name="see-also"></a>Vea también  
 [C++ / CLI manual de migraciones](../dotnet/cpp-cli-migration-primer.md)   
 [Clases y estructuras](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Matrices](../windows/arrays-cpp-component-extensions.md)