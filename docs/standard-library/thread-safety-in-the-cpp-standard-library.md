---
title: Seguridad para subprocesos en la biblioteca estándar de C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 4ac029a119a77fa87c6cd004fece9c4e6b382026
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460063"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Seguridad para subprocesos en la biblioteca estándar de C++

Las siguientes normas de seguridad de subprocesos se aplican a todas las clases de la biblioteca estándar de C++, lo que incluye `shared_ptr`, como se describe a continuación.  A veces se ofrecen mayores garantías, por ejemplo, los objetos iostream estándar, como se describe a continuación, y tipos diseñados específicamente para el multithreading, como los de [\<atomic>](../standard-library/atomic.md).

Un objeto es seguro para subprocesos para leer desde múltiples subprocesos. Por ejemplo, dado un objeto A, es seguro leer A desde el subproceso 1 y desde el subproceso 2 simultáneamente.

Si un subproceso está escribiendo un objeto, todas las lecturas y escrituras a este objeto del mismo subproceso o de otro deben protegerse. Por ejemplo, dado un objeto A, si el subproceso 1 está escribiendo a A, debe evitarse que el subproceso 2 lea o escriba en A.

Es seguro leer y escribir una instancia de un tipo incluso si otro subproceso está leyendo o escribiendo una instancia diferente del mismo tipo. Por ejemplo, dados los objetos A y B del mismo tipo, es seguro que A se esté escribiendo en el subproceso 1 y B se esté leyendo en el subproceso 2.

## <a name="sharedptr"></a>shared_ptr

Varios subprocesos pueden leer y escribir simultáneamente diferentes objetos [shared_ptr](../standard-library/shared-ptr-class.md), incluso cuando los objetos son copias que comparten la propiedad.

## <a name="iostream"></a>iostream

Los objetos iostream estándar `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr` y `wclog` siguen las mismas normas que las otras clases, con esta excepción: se puede escribir en un objeto desde varios subprocesos. Por ejemplo, el subproceso 1 puede escribir en [cout](../standard-library/iostream.md#cout) al mismo tiempo que el subproceso 2. Sin embargo, esto puede causar que la salida de los dos subprocesos se combine.

> [!NOTE]
> Leer desde un búfer de secuencia no se considera una operación de lectura. En lugar de eso, se considera que es una operación de escritura, porque el estado de la clase cambia.

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)
