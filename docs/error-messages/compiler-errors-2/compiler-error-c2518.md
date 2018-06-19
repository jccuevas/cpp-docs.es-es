---
title: Error del compilador C2518 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2518
dev_langs:
- C++
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1e44a99ad49945e441e1560f296dc66568ae3f3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228078"
---
# <a name="compiler-error-c2518"></a>Error del compilador C2518
palabra clave 'palabra clave' no válido en la lista de clases base; pasa por alto  
  
 Las palabras clave `class` y `struct` no deben aparecer en una lista de clases base.  
  
 El ejemplo siguiente genera C2518:  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```