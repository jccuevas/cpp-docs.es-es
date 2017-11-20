---
title: C2696 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2696
dev_langs: C++
helpviewer_keywords: C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70ccaf34a0191f0bd69c95d2cb110f6e6542a6d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2696"></a>C2696 de Error del compilador
No se puede crear un objeto temporal de un tipo administrado 'type'  
  
Las referencias a `const` en un programa no administrado hacen que el compilador llame al constructor y crear un objeto temporal en la pila. Sin embargo, una clase administrada nunca puede crearse en la pila.  
  
Solo es accesible mediante la opción del compilador obsoleta C2696 **/CLR: oldSyntax**.  
