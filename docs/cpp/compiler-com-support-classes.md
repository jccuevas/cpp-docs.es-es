---
title: Clases de compatibilidad con COM del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fe4e7c26d1b32f16d524407279e5e71534d00c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-com-support-classes"></a>Clases de compatibilidad con COM del compilador
**Específicos de Microsoft**  
  
 Las clases estándar se utilizan para proporcionar compatibilidad con algunos de los tipos COM. Las clases se definen en \<comdef.h > y los archivos de encabezado generados a partir de la biblioteca de tipos.  
  
|Clase|Propósito|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|Encapsula el tipo `BSTR` para proporcionar operadores y métodos útiles.|  
|[_com_error](../cpp/com-error-class.md)|Define el objeto de error iniciado por [_com_raise_error](../cpp/com-raise-error.md) en la mayoría de los errores.|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Encapsula punteros de interfaz COM y automatiza las llamadas necesarias a `AddRef`, **versión**, y `QueryInterface`.|  
|[_variant_t](../cpp/variant-t-class.md)|Ajusta la **VARIANT** tipo para proporcionar operadores y métodos útiles.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)   
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)