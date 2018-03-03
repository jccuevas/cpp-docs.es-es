---
title: _bstr_t::wchar_t*, _bstr_t::char* | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs:
- C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8dc91f76e31b124235347d7bef3e95f7cc5bf48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t::wchar_t*, _bstr_t::char*
**Específicos de Microsoft**  
  
 Devuelve los caracteres BSTR como matriz de caracteres estrechos o anchos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      operator const wchar_t*( ) const throw( );   
operator wchar_t*( ) const throw( );   
operator const char*( ) const;   
operator char*( ) const;  
```  
  
## <a name="remarks"></a>Comentarios  
 Estos operadores pueden utilizarse para extraer los datos de caracteres encapsulados por el objeto `BSTR`. La asignación de un nuevo valor al puntero devuelto no modifica los datos BSTR originales.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)