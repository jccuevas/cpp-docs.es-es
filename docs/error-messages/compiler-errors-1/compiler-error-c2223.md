---
title: Error del compilador C2223 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2223
dev_langs:
- C++
helpviewer_keywords:
- C2223
ms.assetid: e4506f0f-0317-4a96-8a90-877a156d7939
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ca3cd091b349536046b0ead8e52805db3dff9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067667"
---
# <a name="compiler-error-c2223"></a>Error del compilador C2223

el operando izquierdo de '-> identificador' debe señalar a struct/union

El operando situado a la izquierda de `->` no es un puntero a una clase, estructura o unión.

Este error puede deberse a un operando izquierdo que sea una variable no definida (por lo tanto, escriba `int`).