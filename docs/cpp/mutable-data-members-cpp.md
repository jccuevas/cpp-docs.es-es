---
title: "Miembros de datos mutables (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "mutable_cpp"
  - "mutable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mutable (palabra clave) [C++]"
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Miembros de datos mutables (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta palabra clave solo se puede aplicar a los miembros de datos no estáticos y no constantes de una clase.  Si se declara un miembro de datos `mutable`, después se permite asignar un valor a este miembro de datos desde una función miembro de tipo **const**.  
  
## Sintaxis  
  
```  
  
mutable member-variable-declaration;  
```  
  
## Comentarios  
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
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)