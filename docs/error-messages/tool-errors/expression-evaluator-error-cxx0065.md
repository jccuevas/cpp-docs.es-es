---
title: Error del evaluador de expresiones CXX0065 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297542"
---
# <a name="expression-evaluator-error-cxx0065"></a>Error del evaluador de expresiones CXX0065
variable de marco de pila es necesario  
  
 Una expresión contiene una variable que existe dentro del ámbito actual, pero no se ha creado aún.  
  
 Este error puede producirse cuando se ha ejecutado en el prólogo de una función, pero aún no configurar el marco de pila para la función, o si se ha ejecutado en el código de salida para la función.  
  
 Paso a paso el código de prólogo hasta que se ha configurado el marco de pila antes de evaluar la expresión.  
  
 Este error es idéntico a CAN0065.