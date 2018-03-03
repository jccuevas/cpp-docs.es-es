---
title: Genericreleasenotifier (Constructor) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5f6f656ff1908dc215efb1fc322b348618a236d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier (Constructor)
Inicializa una nueva instancia de la clase genericreleasenotifier.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `callback`  
 Una expresión lambda, functor o controlador de eventos de puntero a función que se puede invocar con el operador de la función de paréntesis (`()`).  
  
 `release`  
 Especifique `true` para habilitar la llamada subyacente [módulo:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) método; en caso contrario, especifique `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Module::GenericReleaseNotifier (clase)](../windows/module-genericreleasenotifier-class.md)