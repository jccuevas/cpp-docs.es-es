---
title: Miembros de datos mutables (C++) | Documentos de Microsoft
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
ms.openlocfilehash: e7dd639cbf1ef076dee6e447f317533bf12dae10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mutable-data-members-c"></a>Miembros de datos mutables (C++)
Esta palabra clave solo se puede aplicar a los miembros de datos no estáticos y no constantes de una clase. Si se declara un miembro de datos `mutable`, después se permite asignar un valor a este miembro de datos de un **const** función miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, el siguiente código se compilará sin errores porque `m_accessCount` se ha declarado como `mutable` y, por tanto, se puede modificar con `GetFlag` aunque `GetFlag` sea una función miembro de tipo const.  
  
```  
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