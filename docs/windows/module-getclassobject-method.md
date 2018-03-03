---
title: "Module:: GetClassObject (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f234b46da1a70ee0256a9a38ebb2ef7ae0bb5bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject (Método)
Recupera una memoria caché de generadores de clases.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `clsid`  
 Identificador de clase.  
  
 `riid`  
 Identificador de interfaz que se solicita.  
  
 `ppv`  
 Puntero al objeto devuelto.  
  
 `serverName`  
 El nombre del servidor que se especifica en la vista la `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, o `ActivatableClass` macro; o `nullptr` para obtener el nombre del servidor predeterminado.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Use este método solo para COM, no el tiempo de ejecución de Windows. Este método expone solo IClassFactory métodos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)