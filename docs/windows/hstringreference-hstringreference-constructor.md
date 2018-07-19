---
title: Constructor Hstringreference | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc88ea32d4384b36559a4a10da0a5975345bf0d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876012"
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