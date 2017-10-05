---
title: Public (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- public
dev_langs:
- C++
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
caps.latest.revision: 10
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
ms.openlocfilehash: 7ce4262b3f32f48b61e6f4e273ce74c8334f8f0c
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="public-c"></a>public (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
public:  
   [member-list]  
public base-class  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando precede a una lista de miembros de clase, el **público** palabra clave especifica que esos miembros son accesibles desde cualquier función. Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.  
  
 Cuando precede al nombre de una clase base, el **público** palabra clave especifica que los miembros públicos y protegidos de la clase base son públicos y los miembros protegidos, respectivamente, de la clase derivada.  
  
 El acceso predeterminado de miembros de una clase es privado. El acceso predeterminado de miembros de una estructura o unión es público.  
  
 El acceso predeterminado de una clase base es privado para las clases y público para las estructuras. Las uniones no pueden tener clases base.  
  
 Para obtener más información, consulte [privada](../cpp/private-cpp.md), [protegido](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)y la tabla de acceso a miembros de [controlar el acceso a los miembros de clase](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Específicos de /clr  
 En los tipos CLR, C++, obtener acceso a palabras clave de especificador (**público**, `private`, y `protected`) pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte [Control de acceso de miembro](member-access-control-cpp.md).  
  
> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.  
  
## <a name="end-clr-specific"></a>Específicos de END /clr  
  
## <a name="example"></a>Ejemplo  
  
```  
// keyword_public.cpp  
class BaseClass {  
public:  
   int pubFunc() { return 0; }  
};  
  
class DerivedClass : public BaseClass {};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   aBase.pubFunc();       // pubFunc() is accessible   
                          //    from any function  
   aDerived.pubFunc();    // pubFunc() is still public in   
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Controlar el acceso a los miembros de clase](member-access-control-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
