---
title: propiedad (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- property_cpp
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a791615f7fd91a7ccfcda45b23fc524ebd9b6400
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="property-c"></a>propiedad (C++)
**Específicos de Microsoft**  
  
 Este atributo se puede aplicar a los "miembros de datos virtuales" no estáticos en una definición de clase o estructura. El compilador trata a estos "miembros de datos virtuales" como miembros de datos y cambia sus referencias en las llamadas de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   __declspec( property( get=get_func_name ) ) declarator  
   __declspec( property( put=put_func_name ) ) declarator  
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el compilador ve un miembro de datos declarado con este atributo a la derecha de un operador de selección de miembro ("**.**"o"**->**"), convierte la operación a un **obtener** o **colocar** función, dependiendo de si una expresión es un valor l o un valor r. En contextos más complicados, como "`+=`", se realiza una reescritura usan ambos **obtener** y **colocar**.  
  
 Este atributo se puede utilizar también en la declaración de una matriz vacía en una definición de clase o estructura. Por ejemplo:  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 La instrucción anterior indica que `x[]` se puede utilizar con uno o más índices de matriz. En este caso, `i=p->x[a][b]` se convertirá en `i=p->GetX(a, b)` y `p->x[a][b] = i` se convertirá en `p->PutX(a, b, i);`  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="example"></a>Ejemplo  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)