---
title: codecvt_utf16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt/std::codecvt_utf16
- std::codecvt_utf16
- std.codecvt_utf16
- codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8ee859512a6b4a3050eec6f91d4b3c8449cf918a
ms.lasthandoff: 02/24/2017

---
# <a name="codecvtutf16"></a>codecvt_utf16
Representa una faceta [locale](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE o UTF-16BE.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```
## <a name="parameters"></a>Parámetros
`Elem`  
Tipo de elemento de carácter ancho.  
`Maxcode`  
Número máximo de caracteres de la faceta de configuración regional.  
`Mode`  
Información de configuración de la faceta de configuración regional.  

## <a name="remarks"></a>Comentarios
Esta clase de plantilla convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE, si Mode & little_endian, o UTF-16BE en caso contrario.

El flujo de bytes debe escribirse en un archivo binario; puede dañarse si se escribe en un archivo de texto.

## <a name="requirements"></a>Requisitos
Encabezado: \<codecvt> Espacio de nombres: std
