---
title: Error del compilador C2243 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2243
dev_langs: C++
helpviewer_keywords: C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9725239c7e7b8899c23584aa56d26ed77bd757a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2243"></a>Error del compilador C2243
La conversión 'tipo de conversión' de 'tipo1' a 'tipo' existe, pero es inaccesible  
  
 La protección de acceso (`protected` o `private`) ha evitado la conversión de un puntero a una clase derivada en un puntero a la clase base.  
  
 El siguiente ejemplo genera el error C2243:  
  
```  
// C2243.cpp  
// compile with: /c  
class B {};  
class D : private B {};  
class E : public B {};  
  
D d;  
B *p = &d;   // C2243  
  
E e;  
B *p2 = &e;  
```  
  
 Las clases base con acceso `protected` o `private` no son accesibles para los clientes de la clase derivada. Estos niveles de control de acceso se utilizan para indicar que la clase base es un detalle de implementación que debería ser invisible para los clientes. Utilice la derivación pública si desea que los clientes de la clase derivada tengan acceso a la conversión implícita de un puntero de clase derivada en un puntero a la clase base.