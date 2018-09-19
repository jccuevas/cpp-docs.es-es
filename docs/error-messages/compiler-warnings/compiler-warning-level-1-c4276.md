---
title: Compilador advertencia (nivel 1) C4276 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a6c85b460e9718a8816598afb016e9c7a493b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116027"
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276

'function': ningún prototipo proporcionado; supone que no hay parámetros

Cuando tomar la dirección de una función con el [__stdcall](../../cpp/stdcall.md) convención de llamada, se debe indicar un prototipo para el compilador pueda crear el nombre representativo de la función. Puesto que *función* no dispone de ningún prototipo, el compilador, al crear el nombre representativo, asume la función no tiene ningún parámetro.