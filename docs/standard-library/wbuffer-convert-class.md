---
title: wbuffer_convert (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 502b532fc0c2dfe4ba19844b35e6c301c2764a8b
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="wbufferconvert-class"></a>wbuffer_convert (Clase)
Describe un búfer de secuencia que controla la transmisión de elementos a y desde un búfer de secuencia de bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Codecvt`|La faceta [locale](../standard-library/locale-class.md) que representa el objeto de conversión.|  
|`Elem`|Tipo de elemento de carácter ancho.|  
|`Traits`|Los rasgos asociados a *Elem*.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla describe un búfer de secuencia que controla la transmisión de elementos de tipo `_Elem` cuyos rasgos de caracteres se describen por medio de la clase `Traits`, a y desde una secuencia de tipo `std::streambuf`.  
  
 La conversión entre una secuencia de valores `Elem` y las secuencias multibyte se realiza con un objeto de clase `Codecvt<Elem, char, std::mbstate_t>`, que cumple los requisitos de la faceta de conversión de código estándar `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Un objeto de esta clase de plantilla almacena lo siguiente:  
  
-   Un puntero a su búfer de secuencia de bytes subyacente  
  
-   Un puntero al objeto de conversión asignado (que se libera cuando el [wbuffer_convert](../standard-library/wbuffer-convert-class.md)

