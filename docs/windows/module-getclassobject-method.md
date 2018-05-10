---
title: 'Module:: GetClassObject (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9205b04fc27e1c6e0e6133a08c3c2f69ffdfc314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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