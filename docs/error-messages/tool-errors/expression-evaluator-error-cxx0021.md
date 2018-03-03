---
title: Error del evaluador de expresiones CXX0021 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0021
dev_langs:
- C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 475074acf4a01c60fc1108910d5eb41c54b48923
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0021"></a>Error del evaluador de expresiones CXX0021
struct o union utilizadas como escalar  
  
 Se usó una estructura o unión en una expresión, pero no se especificó ningún elemento.  
  
 Al manipular una estructura o unión variable, el nombre de la variable puede aparecer por sí mismo, sin un calificador de campo. Si se utiliza una estructura o unión en una expresión, se deben calificar con el elemento específico deseado.  
  
 Especifique el elemento cuyo valor es que se usará en la expresión.  
  
 Este error es idéntico a CAN0021.