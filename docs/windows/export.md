---
title: exportar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.export
dev_langs: C++
helpviewer_keywords: export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a3229b1cc924c0268bf9a79df53bc18ce2684a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="export"></a>exportar
Hace que una estructura de datos que se colocarán en el archivo IDL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **exportar** C++ atributo da lugar a una estructura de datos que se colocarán en el archivo .idl y, a continuación, esté disponible en la biblioteca de tipos en un formato binario compatible que hace que esté disponible para su uso con cualquier lenguaje.  
  
 No se puede aplicar el **exportar** atributo a una clase, aunque la clase sólo tiene miembros públicos (el equivalente de un `struct`).  
  
 Si exporta sin nombre `enum`s o `struct`s, estarán especificado nombres que comienzan por **__unnamed***x*, donde *x* es un número secuencial.  
  
 Las definiciones de tipo válidos para la exportación son tipos base, estructuras, uniones, enumeraciones, o escriba los identificadores.  Vea [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el **exportar** atributo:  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**Unión**, `typedef`, `enum`, `struct`, o`interface`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
