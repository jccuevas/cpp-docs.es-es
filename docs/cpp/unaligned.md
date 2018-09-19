---
title: __unaligned | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9593a0b3c6e6980f5be2ce9dcf13e505e94dcace
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040208"
---
# <a name="unaligned"></a>__unaligned

**Específico de Microsoft**. Cuando se declara un puntero con el **__unaligned** modificador, el compilador supone que el puntero direcciona datos que no está alineados. Por lo tanto, adecuado para la plataforma de código se genera para controlar las lecturas sin alinear y escribe a través del puntero.

## <a name="remarks"></a>Comentarios

Este modificador describe la alineación de los datos dirigidos por el puntero; se supone que el propio puntero esté alineado.

La necesidad de que el **__unaligned** palabra clave varía según el entorno y la plataforma. Error al marcar adecuadamente los datos puede producir problemas comprendido las penalizaciones de rendimiento y errores de hardware. El **__unaligned** modificador no es válido para el x86 plataforma.

Para obtener más información sobre la alineación, vea:

- [align](../cpp/align-cpp.md)

- [__alignof (Operador)](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)