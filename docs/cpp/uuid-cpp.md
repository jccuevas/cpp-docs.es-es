---
title: "uuid (C++) | Microsoft Docs"
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
  - "uuid"
  - "uuid_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], uuid"
  - "uuid __declspec (palabra clave)"
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El compilador adjunta un GUID a una clase o estructura declarada o definida \(solo definiciones completas de objeto COM\) con el atributo `uuid`.  
  
## Sintaxis  
  
```  
  
__declspec( uuid("  
ComObjectGUID  
") ) declarator  
```  
  
## Comentarios  
 El atributo `uuid` toma una cadena como argumento.  Esta cadena denomina un GUID en formato del Registro normal con o sin los delimitadores **{ }**.  Por ejemplo:  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Este atributo se puede aplicar en un nueva declaración.  Esto permite que los encabezados de sistema suministren las definiciones de interfaces tales como **IUnknown**, y que la nueva declaración en algún otro encabezado \(por ejemplo, COMDEF.H\) suministre el GUID.  
  
 La palabra clave [\_\_uuidof](../cpp/uuidof-operator.md) se puede aplicar para recuperar el GUID de constante asociado a un tipo definido por el usuario.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)