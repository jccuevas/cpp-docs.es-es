---
title: UUID (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b143def4d758307c6ce6737281bdca1097aaa8c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="uuid-c"></a>uuid (C++)
**Específicos de Microsoft**  
  
 El compilador adjunta un GUID a una clase o estructura declarada o definida (solo definiciones completas de objeto COM) con el atributo `uuid`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo `uuid` toma una cadena como argumento. Esta cadena denomina un GUID en formato de registro normal con o sin el **{}** delimitadores. Por ejemplo:  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Este atributo se puede aplicar en un nueva declaración. Esto permite que los encabezados de sistema suministren las definiciones de interfaces tales como **IUnknown**y la nueva declaración en algún otro encabezado (como \<comdef.h >) suministre el GUID.  
  
 La palabra clave [__uuidof](../cpp/uuidof-operator.md) pueden aplicarse para recuperar el GUID de constante asociado a un tipo definido por el usuario.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)