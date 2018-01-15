---
title: Constructor Hstringreference | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs: C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398ea9403f784c30f8e015101c25b071f1d6fb29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference (Constructor)
Inicializa una nueva instancia de la clase HStringReference.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sizeDest`  
 Un parámetro de plantilla que especifica el tamaño del búfer de HStringReference de destino.  
  
 `str`  
 Una referencia a una cadena de caracteres anchos.  
  
 `len`  
 La longitud máxima de la `str` búfer de parámetro para utilizar en esta operación. Si el `len` parámetro no se especifica, toda la matriz `str` se usa el parámetro. Si `len` es mayor que `sizeDest`, `len` está establecido en `sizeDest`-1.  
  
 `other`  
 Otro objeto de HStringReference.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un nuevo objeto de HStringReference el mismo tamaño que el parámetro `str`.  
  
 El segundo constructor inicializa un nuevo HStringReference de objeto que la specifeid de tamaño por parámetro `len`.  
  
 El tercer constructor inicializa un nuevo objeto de HStringReference para el valor de la `other` parámetro y, a continuación, destruye el `other` parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)