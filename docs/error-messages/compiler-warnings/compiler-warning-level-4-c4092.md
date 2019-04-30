---
title: Compilador advertencia (nivel 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: a6949586cf3faa00aafed37a72e58c1b80266cf5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401389"
---
# <a name="compiler-warning-level-4-c4092"></a>Compilador advertencia (nivel 4) C4092

sizeof devuelve 'unsigned long'

El operando de la `sizeof` operador era muy grande, por lo que `sizeof` devuelto unsigned **largo**. Esta advertencia se produce bajo las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). Compatibilidad con ANSI (/Za), el resultado se trunca en su lugar.