---
title: Definir funciones insertadas de C++ con dllexport y dllimport | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 165f110a7464e3393c68a469f1ad1220ef174452
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definir funciones insertadas de C++ con dllexport y dllimport
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Puede definir como alineada una función con el atributo `dllexport`. En este caso, siempre se crean instancias de la función, y siempre se exporta, independientemente de si un módulo del programa hace referencia o no a la función. Se supone que otro programa importa la función.  
  
 También puede definir como alineada una función declarada con el atributo **dllimport**. En este caso, la función se puede expandir (según las especificaciones de /Ob), pero nunca se pueden crear instancias de ella. En concreto, si se toma la dirección de una función alineada importada, se devuelve la dirección de la función que reside en la DLL. Este comportamiento es el mismo que cuando se toma la dirección de una función importada no alineada.  
  
 Estas reglas se aplican a las funciones insertadas cuyas definiciones aparecen dentro de una definición de clase. Además, los datos y cadenas locales estáticos en funciones insertadas mantienen las mismas identidades entre la DLL y el cliente que en un solo programa (es decir, un archivo ejecutable sin interfaz DLL).  
  
 Tome precauciones cuando proporcione funciones insertadas importadas. Por ejemplo, si actualiza la DLL, no suponga que el cliente utilizará la versión modificada de la DLL. Para asegurarse de que se carga la versión correcta, recompile el cliente de DLL también.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)