---
title: Error del evaluador de expresiones CXX0036 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e1bf3cda85d7b3d64d51279688a52cec5c0336
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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