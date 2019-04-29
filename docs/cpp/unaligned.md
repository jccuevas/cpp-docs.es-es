---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 8eb1b93aa55601125600b6c69d9bff3d9ca43aa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244121"
---
# <a name="unaligned"></a>__unaligned

**Específico de Microsoft**. Cuando se declara un puntero con el **__unaligned** modificador, el compilador supone que el puntero direcciona datos que no está alineados. Por lo tanto, adecuado para la plataforma de código se genera para controlar las lecturas sin alinear y escribe a través del puntero.

## <a name="remarks"></a>Comentarios

Este modificador describe la alineación de los datos dirigidos por el puntero; se supone que el propio puntero esté alineado.

La necesidad de que el **__unaligned** palabra clave varía según el entorno y la plataforma. Error al marcar adecuadamente los datos puede producir problemas comprendido las penalizaciones de rendimiento y errores de hardware. El **__unaligned** modificador no es válido para el x86 plataforma.

Para ofrecer compatibilidad con versiones anteriores, **_unaligned** es un sinónimo de **__unaligned** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) se ha especificado.

Para obtener más información sobre la alineación, vea:

- [align](../cpp/align-cpp.md)

- [__alignof (Operador)](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructuras](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)