---
title: TypeName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6eebf038fbe3e5e18e3f2a1e8e7a2aa2554bf41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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