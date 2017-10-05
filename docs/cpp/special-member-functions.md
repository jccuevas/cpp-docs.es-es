---
title: Funciones miembro especiales | Documentos de Microsoft
ms.custom: 
ms.date: 12/06/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 460e6e2ba25566cb4a2295ca4b35590405b51eb3
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="special-member-functions"></a>Funciones miembro especiales  
  
El *funciones miembro especiales* es clase (o struct) funciones de miembro que, en algunos casos, el compilador genera automáticamente para usted. Estas funciones son la [constructor predeterminado](constructors-cpp.md#default_constructors), [destructor](destructors-cpp.md), el [constructor de copias y el operador de asignación de copia](copy-constructors-and-copy-assignment-operators-cpp.md)y el [constructor de movimiento y operador de asignación de movimiento](move-constructors-and-move-assignment-operators-cpp.md). Si la clase no define una o varias de las funciones miembro especiales, el compilador implícitamente puede declarar y definir las funciones que se utilizan. Se llaman a las implementaciones generadas por el compilador la *predeterminado* funciones miembro especiales. El compilador no genera funciones si no son necesarios.  
  
Se puede declarar explícitamente una función miembro especial de forma predeterminada mediante el uso de la `= default` (palabra clave). Esto hace que el compilador definir la función solo si es necesario, de la misma manera que si la función no se declaró en absoluto. 

En algunos casos, el compilador puede generar *eliminado* funciones miembro especiales, que no están definidos y, por tanto, no puede llamar. Esto puede ocurrir en casos donde una llamada a una función miembro especial determinado en una clase no tiene sentido, tiene otras propiedades de la clase. Para evitar explícitamente que la generación automática de una función miembro especial, puede declararlo como eliminado mediante el uso de la `= delete` (palabra clave).  
  
El compilador genera un *constructor predeterminado*, un constructor que no toma ningún argumento, solo cuando no se ha declarado ningún otro constructor. Si se ha declarado únicamente un constructor que toma parámetros, el código que intenta llamar a un constructor predeterminado, el compilador generar un mensaje de error. El constructor predeterminado generado por el compilador realiza simple member-wise [inicialización predeterminada](initializers.md#default_initialization) del objeto. Inicialización predeterminada deja todas las variables de miembro en un estado indeterminado.  
  
El destructor predeterminado realiza automáticamente miembro a miembro a la destrucción del objeto. Es virtual solo si un destructor de clase base es virtual.  
  
La copia de forma predeterminada y la construcción de movimiento y las operaciones de asignación realizan patrón de bits miembro a miembro copia o mueve de miembros de datos no estáticos. Mover las operaciones solo se generan cuando no se declaran ningún destructor u operaciones de mover o copiar. Un constructor de copias predeterminado solo se genera cuando no se declara ningún constructor de copias. Implícitamente se elimina si se declara una operación de movimiento. Un operador de asignación de copia predeterminado se genera solo cuando no se declara explícitamente ningún operador de asignación de copia. Implícitamente se elimina si se declara una operación de movimiento.  
  
## <a name="see-also"></a>Vea también  
[Referencia del lenguaje C++](cpp-language-reference.md)  



 

