---
title: TypeName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
caps.latest.revision: 7
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
ms.openlocfilehash: 95283efc5d3b92a461ba6507e669f6f3e2af2689
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="typename"></a>typename
En las definiciones de plantilla, proporciona una sugerencia al compilador que un identificador desconocido es un tipo. En las listas de parámetros de plantilla, se utiliza para especificar un parámetro de tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
typename identifier;  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta palabra clave se debe usar si un nombre de una definición de plantilla es un nombre completo que depende de un argumento de plantilla; es opcional si el nombre completo no es dependiente. Para obtener más información, consulte [plantillas y resolución de nombres](../cpp/templates-and-name-resolution.md).  
  
 **TypeName** puede utilizarse en cualquier tipo en cualquier parte de una definición o declaración de plantilla. No se permite en la lista de clases base, salvo como argumento de plantilla de una clase base de plantilla.  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 El **typename** palabra clave puede utilizarse en lugar de **clase** en el parámetro de plantilla se enumeran. Por ejemplo, las instrucciones siguientes son semánticamente equivalentes:  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Plantillas](../cpp/templates-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
