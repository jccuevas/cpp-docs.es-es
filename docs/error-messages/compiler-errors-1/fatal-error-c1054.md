---
title: Error irrecuperable C1054 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9daac4944c57dbf08fe0ebcbc95993a97838585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1054"></a>Error irrecuperable C1054
límite del compilador: los inicializadores están demasiado anidados  
  
 El código supera el límite de anidamiento para inicializadores (de 10 a 15 niveles, dependiendo de la combinación de tipos que se está inicializando).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Simplificar los tipos de datos que se va a inicializar para reducir el anidamiento.  
  
2.  Inicialice las variables en instrucciones independientes después de la declaración.