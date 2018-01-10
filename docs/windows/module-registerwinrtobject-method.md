---
title: "Module:: registerwinrtobject (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs: C++
helpviewer_keywords: RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 279a661fae0def63443c9a42d2f290b8d23fa2a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject (Método)
Registra uno o varios objetos en tiempo de ejecución de Windows para que otras aplicaciones puedan conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `serverName`  
 Nombre que especifica un subconjunto de los objetos afectados por esta operación.  
  
 `activatableClassIds`  
 Una matriz de activable CLSID para registrar.  
  
 `cookie`  
 Un valor que identifica los objetos de clase que se registraron. Este valor se utiliza más adelante para revocar el registro.  
  
 `count`  
 El número de objetos que se va a registrar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)