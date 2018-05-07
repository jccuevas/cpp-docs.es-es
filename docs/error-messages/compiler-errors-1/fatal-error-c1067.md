---
title: Error irrecuperable C1067 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ac7084e92f7f2ed496a4c1572e94a4fa46862f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1067"></a>Error irrecuperable C1067
límite del compilador: se superó el límite de tamaño de un registro de tipo de 64 K  
  
 Este error puede producirse si un símbolo tiene un nombre representativo que superen 247 caracteres.  Para resolverlo, acorte el nombre del símbolo.  
  
 Cuando el compilador genera información de depuración, emite registros de tipo para definir tipos encontrados en el código fuente.  Por ejemplo, registros de tipo incluyen estructuras simples y listas de argumentos de funciones.  Algunos de estos registros de tipo pueden ser listas grandes.  
  
 Hay un límite de 64 KB en el tamaño del registro de cualquier tipo.  Este error se producirá si se supera el límite de 64K.  
  
 El error C1067 también se puede producir si hay muchos símbolos con nombres largos o si una clase, estructura o unión tiene demasiados miembros.