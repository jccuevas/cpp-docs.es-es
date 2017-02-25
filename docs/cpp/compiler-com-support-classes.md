---
title: "Clases de compatibilidad con COM del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), compatibilidad con COM"
  - "COM, compatibilidad del compilador"
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de compatibilidad con COM del compilador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Las clases estándar se utilizan para proporcionar compatibilidad con algunos de los tipos COM.  Las clases se definen en los archivos comdef.h y de encabezado generados desde la biblioteca de tipos.  
  
|Clase|Propósito|  
|-----------|---------------|  
|[\_bstr\_t](../cpp/bstr-t-class.md)|Encapsula el tipo `BSTR` para proporcionar operadores y métodos útiles.|  
|[\_com\_error](../cpp/com-error-class.md)|Define el objeto de error producido por [\_com\_raise\_error](../cpp/com-raise-error.md) en la mayoría de los errores.|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-class.md)|Encapsula punteros de interfaz COM y automatiza las llamadas necesarias a `AddRef`, a **Release** y `QueryInterface`.|  
|[\_variant\_t](../cpp/variant-t-class.md)|Encapsula el tipo **VARIANT** para proporcionar operadores y métodos útiles.|  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)   
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)