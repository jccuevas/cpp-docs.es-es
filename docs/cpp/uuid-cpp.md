---
title: UUID (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
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
ms.openlocfilehash: 80975b751b6e167573a038e55042b3546821c68f
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="uuid-c"></a>uuid (C++)
**Específicos de Microsoft**  
  
 El compilador adjunta un GUID a una clase o estructura declarada o definida (solo definiciones completas de objeto COM) con el atributo `uuid`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
__declspec( uuid("  
ComObjectGUID  
") ) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo `uuid` toma una cadena como argumento. Esta cadena denomina un GUID en formato de registro normal con o sin el **{}** delimitadores. Por ejemplo:  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Este atributo se puede aplicar en un nueva declaración. Esto permite que los encabezados de sistema suministren las definiciones de interfaces tales como **IUnknown**y la nueva declaración en algún otro encabezado (por ejemplo, COMDEF. (H) para proporcionar el GUID.  
  
 La palabra clave [__uuidof](../cpp/uuidof-operator.md) pueden aplicarse para recuperar el GUID de constante asociado a un tipo definido por el usuario.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
