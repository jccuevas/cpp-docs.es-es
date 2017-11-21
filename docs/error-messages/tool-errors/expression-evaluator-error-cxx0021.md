---
title: Error del evaluador de expresiones CXX0021 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0021
dev_langs: C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f14a0494ed580f5b9b76c8bf96e55866fc28f654
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0021"></a>Error del evaluador de expresiones CXX0021
struct o union utilizadas como escalar  
  
 Se usó una estructura o unión en una expresión, pero no se especificó ningún elemento.  
  
 Al manipular una estructura o unión variable, el nombre de la variable puede aparecer por sí mismo, sin un calificador de campo. Si se utiliza una estructura o unión en una expresión, se deben calificar con el elemento específico deseado.  
  
 Especifique el elemento cuyo valor es que se usará en la expresión.  
  
 Este error es idéntico a CAN0021.