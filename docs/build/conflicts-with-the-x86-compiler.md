---
title: Conflictos con el compilador de x86
ms.date: 11/04/2016
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
ms.openlocfilehash: e56ebc5631ac5c96a9cdd2dfc2b8e81cdeed9769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614271"
---
# <a name="conflicts-with-the-x86-compiler"></a>Conflictos con el compilador de x86

Tipos de datos que sean mayores que 4 bytes no se alinean automáticamente en la pila cuando se usa el x86 compilador para compilar una aplicación. Dado que la arquitectura para la x86 compilador es una pila alineada de 4 bytes, nada más de 4 bytes, por ejemplo, un entero de 64 bits, no se alinean automáticamente en una dirección de 8 bytes.

Trabajar con datos no alineados tiene dos consecuencias.

- Puede tardar más tiempo en obtener acceso a ubicaciones sin alineación que se tarda en obtener acceso a ubicaciones alineadas.

- Las ubicaciones sin alinear no se puede usar en las operaciones de interbloqueos.

Si necesita una alineación más estricta, use `__declspec(align(N)) on your variable declarations`. Esto hace que el compilador alinear dinámicamente la pila para cumplir sus especificaciones. Sin embargo, ajustar la pila dinámicamente en tiempo de ejecución puede provocar una ejecución más lenta de la aplicación.

## <a name="see-also"></a>Vea también

[Tipos y almacenamiento](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)