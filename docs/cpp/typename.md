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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a276d13172b675cc6856e726cd7139e36fa97d41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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