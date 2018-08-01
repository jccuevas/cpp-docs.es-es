---
title: Miembros de datos mutables (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adc8f9c456d28089d57bc1f13b61ad8efa10b6b6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402925"
---
# <a name="mutable-data-members-c"></a>Miembros de datos mutables (C++)
Esta palabra clave solo se puede aplicar a los miembros de datos no estáticos y no constantes de una clase. Si se declara un miembro de datos **mutable**, es legal para asignar un valor a este miembro de datos desde un **const** función miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, el siguiente código se compilará sin errores porque `m_accessCount` se ha declarado como **mutable**y por lo tanto, se puede modificar mediante `GetFlag` aunque `GetFlag` es una función miembro const.  
  
```cpp 
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)