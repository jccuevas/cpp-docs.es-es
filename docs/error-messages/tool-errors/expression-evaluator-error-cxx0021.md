---
title: Error del evaluador de expresiones CXX0021 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0021
dev_langs:
- C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 996fc46982d809da5e0b37b83f2940102892167e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299372"
---
# <a name="expression-evaluator-error-cxx0021"></a>Error del evaluador de expresiones CXX0021
struct o union utilizadas como escalar  
  
 Se usó una estructura o unión en una expresión, pero no se especificó ningún elemento.  
  
 Al manipular una estructura o unión variable, el nombre de la variable puede aparecer por sí mismo, sin un calificador de campo. Si se utiliza una estructura o unión en una expresión, se deben calificar con el elemento específico deseado.  
  
 Especifique el elemento cuyo valor es que se usará en la expresión.  
  
 Este error es idéntico a CAN0021.