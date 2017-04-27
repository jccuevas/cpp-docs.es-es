---
title: codecvt_utf8 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt_utf8
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 1f6c2724747d22aa662779fa8f6433647a7853f3
ms.lasthandoff: 02/24/2017

---
# <a name="codecvtutf8"></a>codecvt_utf8
Representa una faceta de [configuración regional](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-8.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

`Elem`  
Tipo de elemento de carácter ancho.  
`Maxcode`  
Número máximo de caracteres de la faceta de configuración regional.  
`Mode`  
Información de configuración de la faceta de configuración regional.  

## <a name="remarks"></a>Comentarios

El flujo de bytes puede escribirse en un archivo binario o en un archivo de texto.  

## <a name="requirements"></a>Requisitos

Encabezado: Espacio de nombres <codecvt>: std

