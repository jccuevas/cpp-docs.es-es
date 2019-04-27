---
title: Advertencia del compilador (nivel 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207144"
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276

'function': ningún prototipo proporcionado; supone que no hay parámetros

Cuando tomar la dirección de una función con el [__stdcall](../../cpp/stdcall.md) convención de llamada, se debe indicar un prototipo para el compilador pueda crear el nombre representativo de la función. Puesto que *función* no dispone de ningún prototipo, el compilador, al crear el nombre representativo, asume la función no tiene ningún parámetro.