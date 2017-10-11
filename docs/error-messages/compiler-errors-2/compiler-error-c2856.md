---
title: Error del compilador C2856 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 69b2cdf1e7f3000ef26706c937bff33266ea087a
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2856"></a>Error del compilador C2856
\#pragma hdrstop no puede estar dentro de un bloque #if  
  
 El `hdrstop` pragma no se puede colocar dentro del cuerpo de un bloque de compilación condicional.  
  
 Mover el `#pragma hdrstop` instrucción a un área que no está contenido en un `#if/#endif` bloque.
