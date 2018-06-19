---
title: Error del evaluador de expresiones CXX0017 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7540dc701ffa6e0acb3d2661e1196e5f4552d2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300754"
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