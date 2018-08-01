---
title: protegido (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68cf69cd0c14d56c75a2c67d4369264e7a2ee440
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406177"
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>Sintaxis  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Comentarios  
 El **protegido** palabra clave especifica el acceso a los miembros de clase en el *lista de miembros* hasta el especificador de acceso siguiente (**pública** o **privada**) o el final de la definición de clase. Miembros de clase declarados como **protegido** puede usarse únicamente por lo siguiente:  
  
-   Funciones miembro de la clase que declaró originalmente estos miembros.  
  
-   Objetos friend de la clase que declaró originalmente estos miembros.  
  
-   Clases derivadas con acceso público o protegido desde la clase que declaró originalmente estos miembros.  
  
-   Clases directas derivadas de forma privada que también tienen acceso privado a miembros protegidos.  
  
 Cuando precede al nombre de una clase base, el **protegido** palabra clave especifica que los miembros públicos y protegidos de la clase base son miembros protegidos de sus clases derivadas.  
  
 Los miembros protegidos no son tan privados como **privada** miembros, que son accesibles sólo a los miembros de la clase en el que se declaran, pero no son tan públicos como **pública** miembros, que son accesibles en cualquier función.  
  
 Los miembros protegidos que también se declaran como **estático** son accesibles para cualquier función miembro o friend de una clase derivada. Los miembros protegidos que no se declaran como **estático** son accesibles a sus amigos y funciones de miembro en una clase derivada solo a través de un puntero para hacer referencia a, o un objeto de la clase derivada.  
  
 Para obtener información relacionada, consulte [friend](../cpp/friend-cpp.md), [pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md)y en la tabla de acceso a miembros [controlar el acceso a los miembros de clase](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Específicos de /clr  
 En los tipos CLR, C++, obtener acceso a las palabras clave de especificador (**pública**, **privada**, y **protegido**) pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte [Control de acceso de miembro](member-access-control-cpp.md).  
  
> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.  
  
## <a name="end-clr-specific"></a>Específicos de END /clr  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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