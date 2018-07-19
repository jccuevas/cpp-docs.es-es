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
ms.openlocfilehash: 2a7a9de35e225dabadbf9f4a3731f6d57fd9e99a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940418"
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
