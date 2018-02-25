---
title: wbuffer_convert (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0153bf7d40dbd4290900d15b6e68d84d0c07869
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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
