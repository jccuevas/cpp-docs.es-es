---
title: Crear instancias de plantillas de función | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6374dcd9dad263afd0961be91971d3283ba863ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412129"
---
# <a name="function-template-instantiation"></a>Crear instancias de plantillas de función
Cuando se llama por primera vez a una plantilla de función para cada tipo, el compilador genera una creación de instancias. Cada creación de instancias es una versión de la función con plantilla especializada para el tipo concreto. Se llamará a esta creación de instancias cada vez que se use la función para el tipo. Si tiene varias creaciones de instancias idénticas, incluso en módulos diferentes, solo una copia de la creación de instancias terminará agregándose al archivo ejecutable.  
  
 La conversión de argumentos de función se permite en las plantillas de función de cualquier par de argumento y parámetro en el que el parámetro no dependa de un argumento de plantilla.  
  
 Se pueden crear explícitamente instancias de las plantillas de función si la plantilla se declara con un tipo concreto como argumento. Por ejemplo, se permite el código siguiente:  
  
```cpp
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de función](../cpp/function-templates.md)
