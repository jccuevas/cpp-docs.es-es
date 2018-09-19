---
title: Compilador advertencia (nivel 1) C4041 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085789"
---
# <a name="compiler-warning-level-1-c4041"></a>Advertencia del compilador (nivel 1) C4041

límite del compilador : se va a finalizar el resultado del explorador

La información del explorador supera el límite del compilador.

Esta advertencia puede deberse a la compilación con [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (información del explorador con variables locales).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Compile con /Fr (información del explorador sin variables locales).

1. Deshabilite el resultado del explorador (compile sin /FR o /Fr).