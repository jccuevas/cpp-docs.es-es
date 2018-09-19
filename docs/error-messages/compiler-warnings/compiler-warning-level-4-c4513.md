---
title: Compilador advertencia (nivel 4) C4513 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75ae1c94d7a11fc9bb0049333c65a6677b04778a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087388"
---
# <a name="compiler-warning-level-4-c4513"></a>Advertencia del compilador (nivel 4) C4513

'class': no se pudo generar un destructor

El compilador no puede generar un destructor predeterminado para la clase dada; no se creó ningún destructor. El destructor está en una clase base que no sea accesible para la clase derivada. Si la clase base tiene un destructor privado, hacerla pública o protegida.