---
title: Error del compilador C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 13befc17b94fdf2c22cb84bc64ed55b9375b3473
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165917"
---
# <a name="compiler-error-c3715"></a>Error del compilador C3715

' Pointer ': debe ser un puntero a ' Class '

Ha especificado un puntero en [__hook](../../cpp/hook.md) o [__unhook](../../cpp/unhook.md) que no apuntaba a una clase válida. Para corregir este error, asegúrese de que las llamadas a `__hook` y `__unhook` especifican punteros a clases válidas.
