---
title: '&lt;param&gt; (Visual C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- param
- <param>
dev_langs: C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf74dc4f0488c3c1b41b8ee55c20610684434ee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
La etiqueta \<param> debe usarse en el comentario de una declaración de método para describir uno de los parámetros del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 Nombre de un parámetro de método.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.  
  
 `description`  
 Descripción del parámetro.  
  
## <a name="remarks"></a>Comentarios  
 El texto de la \<param > etiquetas se mostrarán en IntelliSense, el [Examinador de objetos](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)y en el informe Web de comentario de código.  
  
 Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)