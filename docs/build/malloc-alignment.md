---
title: Alineación de malloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa6e2748691eeb8a11834bcf8e6962252be7ab3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712067"
---
# <a name="malloc-alignment"></a>Alineación de malloc

[malloc](../c-runtime-library/reference/malloc.md) garantiza que devuelven memoria que se alinee correctamente para almacenar cualquier objeto que tiene una alineación fundamental y que podría ajustarse a la cantidad de memoria que se asigna. Un *alineación fundamental* es una alineación que es menor o igual que la alineación mayor que sea compatible con la implementación sin una especificación de alineación. (En Visual C++, esta es la alineación necesaria para un `double`, u 8 bytes. En el código destinado a las plataformas de 64 bits, son 16 bytes). Por ejemplo, una asignación de cuatro bytes se alinearía en un límite que admite cualquier objeto de cuatro bytes o menos.

Visual C++ permite tipos que tienen *alineación extendida*, que son también se denomina *demasiado alineados* tipos. Por ejemplo, los tipos SSE [__m128](../cpp/m128.md) y `__m256`y los tipos que se declaran mediante `__declspec(align( n ))` donde `n` es mayor que 8, tienen alineación extendida. Alineación de memoria en un límite que es adecuado para un objeto que requiere alineación extendida no está garantizada por `malloc`. Para asignar memoria para los tipos demasiado alineados, utilice [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) y funciones relacionadas.

## <a name="see-also"></a>Vea también

[Uso de las pilas](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)