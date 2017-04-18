---
title: Error del compilador C3398 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 66bd229369456da18d8bed60b25b6e6b07e03f27
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3398"></a>Error del compilador C3398
'operador': no se puede convertir de 'signatura_de_función' a 'puntero_a_función'. La expresión de origen debe ser un símbolo de función  
  
 Cuando el [__clrcall](../../cpp/clrcall.md) convención de llamada no se especifica cuando se compila con **/CLR**, el compilador genera dos puntos de entrada (direcciones) para cada función, un punto de entrada nativo y un punto de entrada administrado.  
  
 De forma predeterminada, el compilador devuelve el punto de entrada nativo, pero hay algunos casos en los que se desea el punto de entrada administrado (por ejemplo, al asignar la dirección a un puntero a función `__clrcall` ). Para que el compilador elija correctamente el punto de entrada administrado en una asignación, el lado derecho debe ser un símbolo de función.
