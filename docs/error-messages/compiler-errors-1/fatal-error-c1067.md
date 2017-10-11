---
title: Error irrecuperable C1067 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7ef424de5d375f2d198a5f358976d058d556c506
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1067"></a>Error irrecuperable C1067
límite del compilador: se superó el límite de tamaño de un registro de tipo de 64 K  
  
 Este error puede producirse si un símbolo tiene un nombre representativo que superen 247 caracteres.  Para resolverlo, acorte el nombre del símbolo.  
  
 Cuando el compilador genera información de depuración, emite registros de tipo para definir tipos encontrados en el código fuente.  Por ejemplo, registros de tipo incluyen estructuras simples y listas de argumentos de funciones.  Algunos de estos registros de tipo pueden ser listas grandes.  
  
 Hay un límite de 64 KB en el tamaño del registro de cualquier tipo.  Este error se producirá si se supera el límite de 64K.  
  
 El error C1067 también se puede producir si hay muchos símbolos con nombres largos o si una clase, estructura o unión tiene demasiados miembros.
