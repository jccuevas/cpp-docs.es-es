---
title: Error del evaluador de expresiones CXX0036 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdf6ddf412786a53ec8da995c2824274da2da3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0036"></a>Error del evaluador de expresiones CXX0036
contexto {...} errónea especificación  
  
 Este mensaje puede ser generado por cualquiera de varios errores en el uso del operador de contexto (**{}**).  
  
-   La sintaxis del operador de contexto (**{}**) se especificó incorrectamente.  
  
     La sintaxis del operador de contexto es:  
  
     {*función*,*módulo*,*dll*}*expresión*  
  
     Especifica el contexto de *expresión*. El operador de contexto tiene la misma precedencia y uso que una conversión de tipo.  
  
     Las comas finales se pueden omitir. Si cualquiera de *función*, *módulo*, o *dll* contiene una coma literal, debe incluir el nombre completo entre paréntesis.  
  
-   El nombre de la función se ha escrito incorrectamente, o no existe en el módulo especificado o la biblioteca de vínculos dinámicos.  
  
     Dado que C es un lenguaje que distingue mayúsculas de minúsculas, *función* deberán incluirse en las letras mayúsculas y minúsculas como se define en el origen.  
  
-   No se encontró el módulo o DLL.  
  
     Compruebe el nombre de ruta de acceso completa del archivo DLL o módulo especificado.  
  
 Este error es idéntico a CAN0036.