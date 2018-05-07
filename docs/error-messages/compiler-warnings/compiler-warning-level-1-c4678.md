---
title: Compilador advertencia (nivel 1) C4678 | Documentos de Microsoft
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
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4678"></a>Advertencia del compilador (nivel 1) C4678
la clase base 'base_type' es menos accesible que 'derived_type'  
  
Un tipo público se deriva de un tipo privado. Si se crea una instancia del tipo público en un ensamblado al que se ha hecho referencia, los miembros del tipo base privado no estarán accesibles.  
  
Solo es accesible mediante la opción del compilador obsoleta C4678 **/CLR: oldSyntax**. Es un error cuando se usa **/CLR**, tener una clase base que es menos accesible que su clase derivada.  
