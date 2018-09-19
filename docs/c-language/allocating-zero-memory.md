---
title: Asignación de memoria cero | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085061"
---
# <a name="allocating-zero-memory"></a>Asignación de memoria cero

**ANSI 4.10.3** El comportamiento de la función `calloc`, `malloc` o `realloc` si el tamaño solicitado es cero

Las funciones `calloc`, `malloc` y `realloc` aceptan cero como argumento. No se asigna ninguna memoria real, pero se devuelve un puntero válido y el bloque de memoria se puede modificar después mediante realloc.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)