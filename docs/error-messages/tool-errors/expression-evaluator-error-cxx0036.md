---
title: "Error del evaluador de expresiones CXX0036 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0036"
  - "CXX0036"
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del evaluador de expresiones CXX0036
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

especificación de contexto {...} errónea  
  
 Este mensaje puede estar generado por varios errores que utilizan el operador de contexto \(**{}**\).  
  
-   La sintaxis del operador de contexto \(**{}**\) se ha indicado de forma incorrecta.  
  
     La sintaxis del operador de contexto es:  
  
     {*función*,*módulo*,*dll*}*expresión*  
  
     Esto especifica el contexto de *expression*.  El operador de contexto tiene la misma precedencia y uso que una conversión de tipo.  
  
     Las comas finales se pueden omitir.  Si cualquier *función*, *módulo* o *dll* contiene una coma literal, se debe encerrar entre paréntesis todo el nombre.  
  
-   La ortografía del nombre de la función no es correcta, o no existe en el modulo o biblioteca de vínculos dinámicos especificado.  
  
     Dado que C es un lenguaje que distingue entre mayúsculas y minúsculas, *función* debe especificarse en el tipo de letra mayúscula o minúscula exacto a como se defina en el código fuente.  
  
-   No se puede encontrar el módulo o la DLL.  
  
     Compruebe el nombre completo de la ruta de acceso del módulo o DLL especificado.  
  
 Este error es idéntico a CAN00036.