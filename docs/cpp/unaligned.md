---
title: __unaligned | Documentos de Microsoft
ms.custom: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9f30e2b268be6f9398cf0af40d66b786c7cdca9
ms.sourcegitcommit: eb246547c7c9adc7d7ac4083ef09bf6e54dec914
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="unaligned"></a>__unaligned

**Específicos de Microsoft**. Cuando se declara un puntero con el modificador `__unaligned`, el compilador supone que el puntero hace referencia a datos no alineados. Por lo tanto, código adecuado para la plataforma se genera para controlar desalineadas lee y escribe a través del puntero.

## <a name="remarks"></a>Comentarios

Este modificador describe la alineación de los datos al que señala el puntero; se supone que el propio puntero estar alineados.

La necesidad de que el `__unaligned` palabra clave varía según el entorno y la plataforma. Error al marcar adecuadamente los datos puede dar lugar a problemas diversos, desde la reducción de rendimiento para los errores de hardware. El `__unaligned` modificador no es válido para el x86 plataforma.

Para obtener más información sobre la alineación, vea:

- [align](../cpp/align-cpp.md)

- [__alignof (Operador)](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)
