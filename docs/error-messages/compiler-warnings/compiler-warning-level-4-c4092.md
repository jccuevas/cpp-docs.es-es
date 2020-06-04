---
title: ADVERTENCIA del compilador (nivel 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 6786d692785dbca575d4b241b7b3e3d40575b686
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198554"
---
# <a name="compiler-warning-level-4-c4092"></a>ADVERTENCIA del compilador (nivel 4) C4092

sizeof devuelve ' unsigned Long '

El operando del operador `sizeof` era muy grande, por lo que `sizeof` devolvió un **valor Long**sin signo. Esta advertencia se produce en las extensiones de Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)). En compatibilidad con ANSI (/za), el resultado se trunca en su lugar.
