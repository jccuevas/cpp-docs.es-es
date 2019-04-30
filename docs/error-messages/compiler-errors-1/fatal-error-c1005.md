---
title: Error irrecuperable C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: a84791367656729b1cbd50ca180368f6c01531a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383196"
---
# <a name="fatal-error-c1005"></a>Error irrecuperable C1005

cadena demasiado grande para el búfer

Una cadena de un archivo intermedio del compilador ha desbordado un búfer.

Este error puede producirse en caso de que el parámetro pasado a las opciones del compilador [/Fd](../../build/reference/fd-program-database-file-name.md) o [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) sea mayor que 256 bytes.