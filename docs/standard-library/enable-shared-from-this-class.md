---
title: enable_shared_from_this (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- enable_shared_from_this
- std::enable_shared_from_this
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 7f32ee8a40da16ac919f0c3d8be05573f7b78c3a
ms.lasthandoff: 02/24/2017

---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this (Clase)
Ayuda a generar un `shared_ptr`.  
  
## <a name="syntax"></a>Sintaxis  
```    
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
}; 
``` 
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo controlado por el puntero compartido.  
  
## <a name="remarks"></a>Comentarios  
 Los objetos derivados de `enable_shared_from_this` pueden usar los métodos `shared_from_this` en las funciones miembro para crear propietarios [shared_ptr](../standard-library/shared-ptr-class.md) de la instancia que comparte propiedad con propietarios `shared_ptr` existentes. En caso contrario, si crea un nuevo `shared_ptr` mediante `this`, es distinto de los propietarios `shared_ptr` existentes, lo que puede provocar referencias no válidas o que el objeto se elimine más de una vez.  
  
 Los constructores, el destructor y el operador de asignación están protegidos para evitar un uso incorrecto accidental. El tipo de argumento de plantilla `Ty` debe ser el tipo de la clase derivada.  
  
 Para obtener un ejemplo de uso, vea [enable_shared_from_this::shared_from_this](#enable_shared_from_this__shared_from_this).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<memory>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameenablesharedfromthissharedfromthisa--enablesharedfromthissharedfromthis"></a><a name="enable_shared_from_this__shared_from_this"></a>  enable_shared_from_this::shared_from_this  
 Genera un `shared_ptr` que comparte la propiedad de la instancia con propietarios `shared_ptr` existentes.  
  
```  
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Al derivar objetos desde la clase base `enable_shared_from_this`, las funciones miembro de plantilla `shared_from_this` devuelven un objeto [shared_ptr (Clase)](../standard-library/shared-ptr-class.md) que comparte la propiedad de esta instancia con propietarios `shared_ptr` existentes. En caso contrario, si crea un nuevo `shared_ptr` a partir de `this`, es distinto de los propietarios `shared_ptr` existentes, lo que puede provocar referencias no válidas o que el objeto se elimine más de una vez. El comportamiento es indefinido si se llama a `shared_from_this` en una instancia que ya no pertenece a un objeto `shared_ptr`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std_memory_shared_from_this.cpp   
// compile with: /EHsc   
#include <memory>  
#include <iostream>  
  
using namespace std;  
  
struct base : public std::enable_shared_from_this<base>  
{  
    int val;    
    shared_ptr<base> share_more()  
    {  
        return shared_from_this();  
    }  
};  
  
int main()  
{  
    auto sp1 = make_shared<base>();  
    auto sp2 = sp1->share_more();  
  
    sp1->val = 3;  
    cout << "sp2->val == " << sp2->val << endl;    
    return 0;  
}   
```  
  
```Output  
sp2->val == 3  
```  
  
## <a name="see-also"></a>Vea también  
 [enable_shared_from_this::shared_from_this](#enable_shared_from_this__shared_from_this)   
 [shared_ptr (Clase)](../standard-library/shared-ptr-class.md)
