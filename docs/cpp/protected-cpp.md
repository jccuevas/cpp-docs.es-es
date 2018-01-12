---
title: Protected (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: protected_cpp
dev_langs: C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02366a53f02142f66aa5dca493c5460c9f2d1d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Comentarios  
 El `protected` palabra clave especifica el acceso a miembros de clase en el *lista de miembros* hasta el especificador de acceso siguiente (**público** o `private`) o el final de la definición de clase. Los miembros de clase declarados como `protected` solo los pueden utilizar los siguientes elementos:  
  
-   Funciones miembro de la clase que declaró originalmente estos miembros.  
  
-   Objetos friend de la clase que declaró originalmente estos miembros.  
  
-   Clases derivadas con acceso público o protegido desde la clase que declaró originalmente estos miembros.  
  
-   Clases directas derivadas de forma privada que también tienen acceso privado a miembros protegidos.  
  
 Cuando precede al nombre de una clase base, la palabra clave `protected` especifica que los miembros públicos y protegidos de la clase base son miembros protegidos de sus clases derivadas.  
  
 Los miembros protegidos no son tan privados como `private` miembros, que son accesibles únicamente a los miembros de la clase en el que se declaran, pero no son tan públicos como **público** miembros, que son accesibles en cualquier función.  
  
 Los miembros protegidos que también se declaran como **estático** son accesibles a cualquier función miembro o friend de una clase derivada. Los miembros protegidos que no se declaran como **estático** son accesibles a sus amigos y funciones de miembro en una clase derivada solo a través de un puntero para hacer referencia a, o un objeto de la clase derivada.  
  
 Para obtener información relacionada, consulte [friend](../cpp/friend-cpp.md), [público](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md)y la tabla de acceso a miembros de [controlar el acceso a los miembros de clase](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Específicos de /clr  
 En los tipos CLR, C++, obtener acceso a palabras clave de especificador (**público**, `private`, y `protected`) pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte [Control de acceso de miembro](member-access-control-cpp.md).  
  
> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.  
  
## <a name="end-clr-specific"></a>Específicos de END /clr  
  
## <a name="example"></a>Ejemplo  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Controlar el acceso a los miembros de clase](member-access-control-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)