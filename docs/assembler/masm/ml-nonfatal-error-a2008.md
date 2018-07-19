---
title: Error recuperable A2008 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50f7329f698d23f875a29bc316067c39e8d1b8c1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055224"
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