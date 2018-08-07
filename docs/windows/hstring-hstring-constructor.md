---
title: Constructor de hstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96b77ec87e3219206d353f56293fc201c46f5d7e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568776"
---
# <a name="hstringhstring-constructor"></a>HString::HString (Constructor)
Inicializa una nueva instancia de la **HString** clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *HSTR*  
 Un identificador HSTRING.  
  
 *other*  
 Existente **HString** objeto.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un nuevo **HString** objeto que está vacía.  
  
 El segundo constructor inicializa una nueva **HString** objeto por el valor de la existente *otros* parámetro y, a continuación, se destruye el *otros* parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)