---
title: Error recuperable A2008 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef8194fea15f9ebfa65201d43ddbdda2b61786
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2008"></a>Error recuperable A2008 de ML
**error de sintaxis:**  
  
 Un símbolo (token) en la ubicación actual produjo un error de sintaxis.  
  
 Puede haberse producido uno de los siguientes:  
  
-   Un prefijo de punto se agregó o se omite en una directiva.  
  
-   Una palabra reservada (como **C** o **tamaño**) se utiliza como identificador.  
  
-   Se utilizó una instrucción que no estaba disponible con la selección actual del procesador o coprocesador.  
  
-   Un operador de tiempo de ejecución de comparación (como `==`) se utiliza en una instrucción de ensamblado condicional en lugar de un operador relacional (como [EQ](../../assembler/masm/operator-eq.md)).  
  
-   Una instrucción o la directiva se proporcionó operandos insuficientes.  
  
-   Se usó una directiva obsoleta.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)