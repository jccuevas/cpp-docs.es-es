---
title: Palabras clave de herencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
dev_langs:
- C++
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
caps.latest.revision: 9
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
ms.openlocfilehash: 6286d8e3082f0a4a3ce3e00fb3de1ad4ca41589a
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="inheritance-keywords"></a>Palabras clave de herencia
**Específicos de Microsoft**  
  
```  
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;  
```  
  
 donde:  
  
 *nombre de clase*  
 Nombre de la clase que se está declarando.  
  
 C++ permite declarar un puntero a un miembro de clase antes de la definición de clase. Por ejemplo:  
  
```  
class S;  
int S::*p;  
```  
  
 En el código anterior, `p` se declara como un puntero a miembro entero de clase S. Sin embargo, `class S` tiene no se ha definido en este código; solo se ha declarado. Cuando el compilador encuentra un puntero así, debe crear una representación generalizada del puntero. El tamaño de la representación depende del modelo de herencia especificado. Hay cuatro maneras de especificar un modelo de herencia al compilador:  
  
-   En el IDE bajo **representación de puntero a miembro**  
  
-   En la línea de comandos utilizando la [/vmg](../build/reference/vmb-vmg-representation-method.md) cambiar  
  
-   Mediante el [pointers_to_members](../preprocessor/pointers-to-members.md) pragma  
  
-   Mediante las palabras clave de herencia `__single_inheritance`, `__multiple_inheritance` y `__virtual_inheritance`. Esta técnica controla el modelo de herencia clase por clase.  
  
    > [!NOTE]
    >  Si siempre se declara un puntero a un miembro de una clase después de definir la clase, no se necesita usar ninguna de estas opciones.  
  
 Declarar un puntero a un miembro de una clase antes de la definición de clase afecta al tamaño y la velocidad del archivo ejecutable resultante. Cuanto más compleja es la herencia usada por una clase, mayor será el número de bytes necesarios para representar un puntero a un miembro de la clase y cuando mayor es el código necesario para interpretar el puntero. La herencia única es la menos compleja y la herencia virtual la más compleja.  
  
 Si se cambia el ejemplo anterior a:  
  
```  
class __single_inheritance S;  
int S::*p;  
```  
  
 independientemente de las opciones de la línea de comandos o las pragmas, los punteros a miembros de `class S` usarán la representación más pequeña posible.  
  
> [!NOTE]
>  La misma declaración adelantada de una representación de puntero a miembro de la clase debe aparecer en cada unidad de traducción que declare punteros a miembros de esa clase y la declaración debe aparecer antes de que se declaren los punteros a miembros.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)
