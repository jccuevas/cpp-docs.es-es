---
title: "typename | Microsoft Docs"
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
  - "typename"
  - "typename_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typename (especificador de plantilla)"
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typename
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al compilador que un identificador desconocido es un tipo.  
  
## Sintaxis  
  
```  
  
typename identifier;  
```  
  
## Comentarios  
 Utilice esta palabra clave solo en definiciones de plantilla.  
  
 Esta palabra clave se debe usar si el nombre es un nombre completo dependiente de un argumento de plantilla; es opcional si el nombre completo no es dependiente.  Para obtener más información, vea [Plantillas y resolución de nombres](../cpp/templates-and-name-resolution.md).  
  
 **typename** se puede usar en cualquier tipo en cualquier lugar de una declaración o definición de plantilla.  No se permite en la lista de clases base, salvo como argumento de plantilla de una clase base de plantilla.  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 La palabra clave **typename** también se puede usar en lugar de **class** en las listas de parámetros de plantilla.  Por ejemplo, las siguientes instrucciones son idénticas:  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## Ejemplo  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## Vea también  
 [Plantillas](../cpp/templates-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)