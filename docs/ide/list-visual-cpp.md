---
title: '&lt;lista&gt; (Visual C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs: C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e04fb5f7ff2ba22b53c0fe163455bfdb666f9b9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltlistgt-visual-c"></a>&lt;lista&gt; (Visual C++)
El bloque \<listheader> se usa para definir la fila de encabezado de una tabla o de una lista de definiciones. Cuando se define una tabla, solo es necesario suministrar una entrada para un término en el encabezado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `term`  
 Término que se define en `description`.  
  
 `description`  
 Elemento de una lista numerada o con viñetas, o definición de un `term`.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento de la lista se especifica con un bloque \<item>. Cuando se crea una lista de definiciones, se deberán especificar tanto `term` como `description`. En cambio, para una tabla, lista con viñetas o lista numerada, solo es necesario suministrar una entrada para `description`.  
  
 Una lista o una tabla pueden tener tantos bloques \<item> como sean necesarios.  
  
 Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)