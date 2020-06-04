---
title: Error del compilador C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201934"
---
# <a name="compiler-error-c2834"></a>Error del compilador C2834

' operator Operator ' debe estar calificado globalmente

Los operadores `new` y `delete` están vinculados a la clase donde residen. No se puede usar la resolución de ámbito para seleccionar una versión de `new` o `delete` de una clase diferente. Para implementar varias formas del operador `new` o `delete`, cree una versión del operador con parámetros formales adicionales.
