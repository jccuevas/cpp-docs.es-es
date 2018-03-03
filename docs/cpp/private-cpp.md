---
title: Private (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baa3a23eacc8428bcbeb6ee5a88a835ff193ee02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando precede a una lista de miembros de clase, la palabra clave `private` especifica que esos miembros son accesibles solo desde funciones miembro y friend de la clase. Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.  
  
 Cuando precede al nombre de una clase base, la palabra clave `private` especifica que los miembros públicos y protegidos de la clase base son miembros privados de la clase derivada.  
  
 El acceso predeterminado de miembros de una clase es privado. El acceso predeterminado de miembros de una estructura o unión es público.  
  
 El acceso predeterminado de una clase base es privado para las clases y público para las estructuras. Las uniones no pueden tener clases base.  
  
 Para obtener información relacionada, consulte [friend](../cpp/friend-cpp.md), [público](../cpp/public-cpp.md), [protegido](../cpp/protected-cpp.md)y en la tabla de acceso a miembros [controlar el acceso a los miembros de clase](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>Específicos de /clr  
 En los tipos CLR, C++, obtener acceso a palabras clave de especificador (**público**, `private`, y `protected`) pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte [Control de acceso de miembro](member-access-control-cpp.md).  
  
> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.  
  
## <a name="end-clr-specific"></a>Específicos de END /clr  
  
## <a name="example"></a>Ejemplo  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Controlar el acceso a los miembros de clase](member-access-control-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)