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
ms.openlocfilehash: 1090a0f3345f749a2afbd80566a9af7b9ea32d53
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857260"
---
# <a name="__unaligned"></a>__unaligned

**Específico de Microsoft**. Cuando se declara un puntero con el modificador **__unaligned** , el compilador supone que el puntero direcciona datos que no están alineados. Por consiguiente, se genera código adecuado para la plataforma para controlar las lecturas y escrituras sin alinear a través del puntero.

## <a name="remarks"></a>Notas

Este modificador describe la alineación de los datos direccionados por el puntero; se supone que el propio puntero está alineado.

La necesidad de la palabra clave **__unaligned** varía según la plataforma y el entorno. Si no se marcan correctamente los datos, pueden producirse problemas que van desde penalizaciones de rendimiento a errores de hardware. El modificador **__unaligned** no es válido para la plataforma x86.

Por compatibilidad con versiones anteriores, **_unaligned** es un sinónimo de **__unaligned** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

Para obtener más información sobre la alineación, vea:

- [align](../cpp/align-cpp.md)

- [__alignof (Operador)](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructuras](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)