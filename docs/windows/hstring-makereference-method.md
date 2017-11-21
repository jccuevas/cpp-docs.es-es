---
title: "Hstring:: Makereference (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs: C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 026b036e3a4dad0fb88600cb64ac3da892eba2b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="hstringmakereference-method"></a>HString::MakeReference (Método)
Crea un objeto HStringReference de un parámetro de cadena especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sizeDest`  
 Un parámetro de plantilla que especifica el tamaño del búfer de HStringReference de destino.  
  
 `str`  
 Una referencia a una cadena de caracteres anchos.  
  
 `len`  
 La longitud máxima de la `str` búfer de parámetro para utilizar en esta operación. Si el `len` parámetro no se especifica, toda la matriz `str` se usa el parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 HStringReference objeto cuyo valor es el mismo que el especificado `str` parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)