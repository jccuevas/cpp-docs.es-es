---
title: "&lt;excepción&gt; (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c07dde806938b38dd55a3258b3724b0937d5601d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltexceptiongt-visual-c"></a>&lt;excepción&gt; (Visual C++)
La etiqueta \<exception> le permite especificar qué excepciones se pueden producir. Esta etiqueta se aplica a una definición de método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `member`  
 Una referencia a una excepción que está disponible desde el entorno de compilación actual. Usa reglas de búsqueda de nombre, el compilador comprueba si la excepción dada existe y traduce `member` al nombre de elemento canónico en el resultado XML.  El compilador emite una advertencia si no encuentra `member`.  
  
 Ponga el nombre entre comillas simples o dobles.  
  
 Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](../ide/see-visual-cpp.md).  
  
 `description`  
 Una descripción.  
  
## <a name="remarks"></a>Comentarios  
 Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.  
  
 El compilador de Visual C++ intentará resolver referencias cref en un paso por los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [ \<seealso >](../ide/seealso-visual-cpp.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)