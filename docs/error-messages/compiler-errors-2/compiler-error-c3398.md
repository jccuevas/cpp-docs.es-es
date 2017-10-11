---
title: Error del compilador C3398 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 54241a6e57bdfd8795d6f894a1410c1e6c90cf49
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3398"></a>Error del compilador C3398
'operador': no se puede convertir de 'signatura_de_función' a 'puntero_a_función'. La expresión de origen debe ser un símbolo de función  
  
 Si no se especifica la convención de llamada [__clrcall](../../cpp/clrcall.md) cuando se compila con **/clr**, el compilador genera dos puntos de entrada (direcciones) para cada función, un punto de entrada nativo y un punto de entrada administrado.  
  
 De forma predeterminada, el compilador devuelve el punto de entrada nativo, pero hay algunos casos en los que se desea el punto de entrada administrado (por ejemplo, al asignar la dirección a un puntero a función `__clrcall` ). Para que el compilador elija correctamente el punto de entrada administrado en una asignación, el lado derecho debe ser un símbolo de función.
