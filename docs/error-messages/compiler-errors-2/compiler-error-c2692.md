---
title: Error del compilador C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177097"
---
# <a name="compiler-error-c2692"></a>Error del compilador C2692

' function_name ': funciones totalmente prototipos necesarias en el compilador de C con la opción '/CLR '

Al compilar para código administrado de .NET, el compilador de C requiere declaraciones de función ANSI. Además, si una función no toma ningún parámetro, debe declarar explícitamente `void` como el tipo de parámetro.
