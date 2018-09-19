---
title: Error irrecuperable C1005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 888bdaf2eaddc0d4178affa1ccc4ae77c34f4617
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092315"
---
# <a name="fatal-error-c1005"></a>Error irrecuperable C1005

cadena demasiado grande para el búfer

Una cadena de un archivo intermedio del compilador ha desbordado un búfer.

Este error puede producirse en caso de que el parámetro pasado a las opciones del compilador [/Fd](../../build/reference/fd-program-database-file-name.md) o [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) sea mayor que 256 bytes.