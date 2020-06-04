---
title: Error del compilador C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202376"
---
# <a name="compiler-error-c2708"></a>Error del compilador C2708

' Identifier ': la longitud de los parámetros reales en bytes es distinta de la llamada o referencia anterior

Una función [__stdcall](../../cpp/stdcall.md) debe ir precedida de un prototipo. De lo contrario, el compilador interpreta la primera llamada a la función como un prototipo y este error se produce cuando el compilador encuentra una llamada que no coincide.

Para corregir este error, agregue un prototipo de función.
