---
title: Error del evaluador de expresiones CXX0017 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0017
dev_langs: C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e769e9886168c9f19ad110c48d848a9b84ab8aac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0017"></a>Error del evaluador de expresiones CXX0017
no se encontró el símbolo  
  
 No se pudo encontrar un símbolo especificado en una expresión.  
  
 Una posible causa de este error es un error de coincidencia de mayúscula en el nombre del símbolo. Dado de C y C++ son lenguajes entre mayúsculas y minúsculas, un nombre de símbolo debe especificarse en mayúsculas y minúsculas en el que se define en el origen.  
  
 Este error puede producirse al intentar convertir el tipo de una variable con el fin de ver la variable durante la depuración. El `typedef` declara un nuevo nombre para un tipo, pero no define un nuevo tipo. La conversión de tipo intentan en el depurador requiere el nombre de un tipo definido.  
  
 Este error es idéntico a CAN0017.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Asegúrese de que el símbolo ya se ha declarado en el punto en el programa donde se va a utilizar.  
  
2.  Utilice un nombre de tipo real para convertir variables en el depurador, en lugar de un `typedef`-definido por nombre.