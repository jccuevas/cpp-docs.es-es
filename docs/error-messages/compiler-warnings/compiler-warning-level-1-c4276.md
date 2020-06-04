---
title: Advertencia del compilador (nivel 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175823"
---
# <a name="compiler-warning-level-1-c4276"></a>Advertencia del compilador (nivel 1) C4276

' función ': no se ha proporcionado ningún prototipo; se supone que no hay parámetros

Al tomar la dirección de una función con la Convención de llamada de [__stdcall](../../cpp/stdcall.md) , debe proporcionar un prototipo para que el compilador pueda crear el nombre representativo de la función. Puesto que la *función* no tiene ningún prototipo, el compilador, al crear el nombre representativo, supone que la función no tiene parámetros.
