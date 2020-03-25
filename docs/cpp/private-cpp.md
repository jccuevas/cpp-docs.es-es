---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 002a8ad2887bd711bc3654d8e8910e2bede889d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177565"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Sintaxis

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Observaciones

Cuando precede a una lista de miembros de clase, la palabra clave **Private** especifica que esos miembros son accesibles solo desde las funciones miembro y amigos de la clase. Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.

Cuando precede al nombre de una clase base, la palabra clave **Private** especifica que los miembros públicos y protegidos de la clase base son miembros privados de la clase derivada.

El acceso predeterminado de miembros de una clase es privado. El acceso predeterminado de miembros de una estructura o unión es público.

El acceso predeterminado de una clase base es privado para las clases y público para las estructuras. Las uniones no pueden tener clases base.

Para obtener información relacionada, vea [Friend](../cpp/friend-cpp.md), [Public](../cpp/public-cpp.md), [Protected](../cpp/protected-cpp.md)y la tabla de acceso a miembros en [controlar el acceso a los miembros de clase](member-access-control-cpp.md).

## <a name="clr-specific"></a>Específicos de /clr

En los tipos CLR, C++ las palabras clave del especificador de acceso (**Public**, **Private**y **Protected**) pueden afectar a la visibilidad de los tipos y métodos con respecto a los ensamblados. Para obtener más información, vea [Access Control miembro](member-access-control-cpp.md).

> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.

## <a name="end-clr-specific"></a>Específicos de END /clr

## <a name="example"></a>Ejemplo

```cpp
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

## <a name="see-also"></a>Consulte también

[Controlar el acceso a los miembros de clase](member-access-control-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
