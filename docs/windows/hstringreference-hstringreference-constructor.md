---
title: Constructor Hstringreference | Microsoft Docs
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
ms.openlocfilehash: 7dce8c6fca14ad26665bf4868681234374c20f85
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608149"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference (Constructor)
Inicializa una nueva instancia de la **HStringReference** clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *sizeDest*  
 Un parámetro de plantilla que especifica el tamaño del destino **HStringReference** búfer.  
  
 *str*  
 Una referencia a una cadena de caracteres anchos.  
  
 *Len*  
 La longitud máxima de la *str* búfer de parámetro para utilizar en esta operación. Si el *len* parámetro no se especifica, toda la *str* se usa el parámetro. Si *len* es mayor que *sizeDest*, *len* está establecido en *sizeDest*-1.  
  
 *other*  
 Otro **HStringReference** objeto.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un nuevo **HStringReference** objeto que el mismo tamaño que el parámetro *str*.  
  
 El segundo constructor inicializa una nueva **HStringReference** objeto al que el specifeid tamaño por parámetro *len*.  
  
 El tercer constructor inicializa una nueva **HStringReference** objeto por el valor de la *otros* parámetro y, a continuación, se destruye el *otros* parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)