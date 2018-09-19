---
title: Del compilador (nivel 1) de la advertencia C4678 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81eb7df618f97300c2654cc0f4f7a58d18215b26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076104"
---
# <a name="compiler-warning-level-1-c4678"></a>Advertencia del compilador (nivel 1) C4678

la clase base 'base_type' es menos accesible que 'derived_type'

Un tipo público se deriva de un tipo privado. Si se crea una instancia del tipo público en un ensamblado al que se ha hecho referencia, los miembros del tipo base privado no estarán accesibles.

Solo es accesible a través de la opción del compilador obsoleto C4678 **/CLR: oldSyntax**. Es un error al usar **/CLR**, para que tenga una clase base que es menos accesible que su clase derivada.
