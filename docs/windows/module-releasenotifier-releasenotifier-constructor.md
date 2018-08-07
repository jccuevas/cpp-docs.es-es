---
title: Releasenotifier (Constructor) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93dca0500971f0bcfdefd017457e02bf6a033660
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608474"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier (Constructor)
Inicializa una nueva instancia de la **releasenotifier** clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *release*  
 **True** para eliminar esta instancia cuando la `Release` se llama al método; **false** no eliminar esta instancia.  
  
## <a name="exceptions"></a>Excepciones  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Module::ReleaseNotifier (clase)](../windows/module-releasenotifier-class.md)