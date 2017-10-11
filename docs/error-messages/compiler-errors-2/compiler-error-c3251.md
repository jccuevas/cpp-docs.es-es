---
title: Error del compilador C3251 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3251
dev_langs:
- C++
helpviewer_keywords:
- C3251
ms.assetid: 541c163e-5ee9-457c-a1e5-da860788b10d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f17f45a35f9ddd1b3270b484a49c603bee92f8f7
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3251"></a>Error del compilador C3251
no se puede invocar el método de clase base en una instancia de tipo de valor  
  
 El siguiente error se produce porque `GetClass` es un miembro de `Microsoft.Runtime.Object`, no de `Microsoft.Runtime.Integer4`.
